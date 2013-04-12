# Unit Testing

��Ԫ���ԵĶ�����ǰ�����Ӧ����СƬ�ɲ��ԵĴ���Ӵ�����и��룬Ȼ�����������Ϊ�Ƿ��������һ�¡�

һ������Ϊ'��'���Ե�Ӧ�ã������Թ�����Ӧ���зֿ��ĵ�Ԫ���ԣ�����֤��ͬ�����������ȷ�ԡ����в���Ӧ���ڹ������֮ǰ���롣������ÿ������޸�һ������ʱ��ͨ����Ԫ����ȷ�������޸��Ƿ���������⣬�����������������ġ�

һ��������ĵ�Ԫ�������ӣ���������Ҫ���Դ���ָ����value�oһ��sum�����䷵�ؽ���Ƿ���ȷ���������Ȿ���йص����Ӿ��ǣ�������Ҫ����һ���û����һ���µ�Todo��б��У��Ƿ������һ��ָ�����͵�Model��Todos Collection��

�����ִ���webӦ��ʱ��ͨ����Ϊ��õ�ʵ����ʽ���ڿ��������������Զ��ĵ�Ԫ���ԡ��������ǹ�ע��ʹ��Jasmine�ķ�������ȻҲ�кܶ�����ѡ��ֵ�ÿ��ǣ�����QUnit��

# Jasmine

## ��Ϊ-��������

��һ�ڣ����ǻὲ�����ʹ��һ�����еĲ��Կ��[Jasmine](http://pivotal.github.com/jasmine/)������BackboneӦ�ã�����������Pivotal Labs��

Jasmine�Գ���һ�����ڲ���JavaScript�������Ϊ-��������(Behavior-Driven Development��BDD)�Ŀ�ܡ��ڿ�ʼʹ��������֮ǰ����������Ū�����ʲô��[BDD](http://en.wikipedia.org/wiki/Behavior_Driven_Development)��

BDD��һ�ֵڶ������Է�������[Dan North](http://dannorth.net/introducing-bdd/) (BDD�����Ȩ��)�״ζ��壬������ͼ�����������Ϊ����֮Ϊ�ڶ�������Ϊ���뷨�����������������(Domain driven design��DDD)�;������������ͨ�������ݹ����лش������������������������ŶӲ����������������������ͨ����������ĵ��Ͳ��ԡ�

����Ķ���һ������BDD���鼮���п������ᱻ������'���⼰�ڵġ�������(pull)��(outside-in and pull-based)'��ԭ��������Ӿ������������pull���ԣ� ͨ��a) ע��ϵͳ��Ԥ�����(outputs),b) ȷ����Щ������ﵽ����2������Ч��ȷ����������ȷ�����������

BDD�����һ����Ŀ��ͨ���ж�Ԫ�����岢��ϵͳ����ֻ��һ����һ�������û�����Щ��ͬ��Ⱥ�壬�����Բ�ͬ����ʽӰ������д��������������ϵͳ�������������ǵ����������в�ͬ����⡣���ԣ�Ҫ���׶���������˭����������ֵ�Լ����������Ǵ���ʲô��ֵ�����ǳ���Ҫ��

���BDD�������Զ�����һ�������������������������Ŷӿ��ܾͻᶨ�ڵļ���������Ĺ����Ƿ�������������һ�¡�Ϊ�˴ٽ�Ч�ʣ����������Ҫ�Զ���ɡ�BDDIn order to facilitate this efficiently, the process has to be automated. BDD�����������Զ������ԣ���Jasmine������һ��������µĹ��ߡ�

BDD���԰��������ߺͷǼ��������������������


* ���õ����������������ģʽ
* �Ѳ��������Էǿ�����ԱҲ�ܶ����ķ�ʽ�������
* ��������С����д�ļ������뵽ҵ��������֮���ת����

�����ζ�ſ�����Ҫ��Jasmine��Ԫ���Ը���Ŀ�������������չʾ��Ȼ�������ڹ�����Ҫ���������;��

�����߾���������һ�ֲ��Է���[TDD](http://en.wikipedia.org/wiki/Test-driven_development) (test-driven development)һ����ʵʩBDD��TDD�������Ҫ�۵㣺

* ��д��Ԫ����������Ĵ�����Ҫ֧�ֵĹ���
* ������Щ����ʧ��(��ΪҪ֧����Щ���ܵĴ���д��)
* ��д�����ò���ͨ��
* �����ظ����ع�

��һ�����ǽ����������ַ�ʽ(BDD��TDD)��ΪBackboneӦ�ñ�д��Ԫ���ԡ�

***��ʾ*** �ҿ����ܶ࿪������Ȼ������ɱ���֮��ű�д����������֤����Ȼ��Ҳ�������������׵������룬��ֻ�ܲ��Ե������ڴ�����֧�ֵ���Ϊ������һ��������������ԭ�������Ҫ֧�ֵĹ��ܡ�


##Suites, Specs & Spies

ʹ��Jasmineʱ��Ҫ��дsuites(�׼�)��specs(specifications�����˵��)��Suites��Ҫ����������specs��������Щ����l��Ҫ��Щʲô��

ÿ��spec����һ��һ��JavaScript����������```it()```������������һ�������ַ�����һ��function��������Ҫ������ָ����Ԫ�����չ�ֽ�����μ�BDD�Ĺ������Ӧ�������塣������һ���򵥵����ӣ�

```javascript
it('should be incrementing in value', function(){
    var counter = 0;
    counter++;
});
```

���䱾����ԣ�һ��spec���û��������Ϊ��������������û��ʲô�ô��ˡ�ʹ��```expect()```������[expectation matcher](https://github.com/pivotal/jasmine/wiki/Matchers) (����```toEqual()```, ```toBeTruthy()```, ```toContain()```)���������������ʾ����

```javascript
it('should be incrementing in value', function(){
    var counter = 0;
    counter++;
    expect(counter).toEqual(1);
});
```

��������ж�```counter```������ֵҪ����1�����ִ���������ǳ���(ƾֱ���Ϳ�������ˣ������κν���)��

һ��Specs�͹�����suites��ͨ��Jasmine��```describe()```�������壬����һ�������ַ�����һ��������suite�����ƻ�������ͨ������Ҫ���Ե��������ģ�顣

Jasmine�������Ϊ��������ʱ����specs�ķ������ơ�������һ���򵥵�ʾ����

```javascript
describe('Stats', function(){
    it('can increment a number', function(){
        ...
    });

    it('can subtract a number', function(){
        ...
    });
});
```

Suites����һ�����������Կ�����describe���������������� specs��ĺ���Ҳ���Է��ʵ���

```javascript
describe('Stats', function(){
    var counter = 1;

    it('can increment a number', function(){
        // the counter was = 1
        counter = counter + 1;
        expect(counter).toEqual(2);
    });

    it('can subtract a number', function(){
        // the counter was = 2
        counter = counter - 1;
        expect(counter).toEqual(1);
    });
});
```

***��ʾ��*** Suites�ǰ��䶨���˳��ִ�У������Ҫ������Ӧ�ò��Ա����ĳ���ض����ֵĲ��Խ��������ܷǳ����á�

Jasmineͬ��֧��**spies(����)** �����ڵ�Ԫ������һ��ģ�£����ӣ���α����Ϊ�ķ�����Spies���滻���Ǽ��ӵĺ���������ģ��������Ҫα�����Ϊ��

��������������У�������һ�������Todo function����```setComplete```���������Դ���Ĳ����Ƿ����������

```javascript
var Todo = function(){
};

Todo.prototype.setComplete = function (arg){
    return arg;
}

describe('a simple spy', function(){
    it('should spy on an instance method of a Todo', function(){
        var myTodo = new Todo();
        spyOn(myTodo, 'setComplete');
        myTodo.setComplete('foo bar');

        expect(myTodo.setComplete).toHaveBeenCalledWith('foo bar');

        var myTodo2 = new Todo();
        spyOn(myTodo2, 'setComplete');

        expect(myTodo2.setComplete).not.toHaveBeenCalled();

    });
});
```

���п��ܻ��õ�spies�ĵط��ǲ���[asynchronous(�첽)](http://en.wikipedia.org/wiki/Asynchronous_communication)��Ϊ������AJAX����Jasmine֧�֣�

* ʹ��spiesģ��AJAX��������д���ԡ�������AJAX����֮ǰ������֮�����в��Դ��롣Ҳ����α��������˵���Ӧ���������͵Ĳ��Ժô����Ǹ��죬����Ҫ�ȴ�ʵ�ʵķ��������á�
* �첽���Բ���Ҫ����spies

��һ�ֲ��ԣ�����α��AJAX������֤�����URL�Ƿ���ȷ�Լ�ִ�лص�������еĻ���

```javascript
it("the callback should be executed on success", function () {
    spyOn($, "ajax").andCallFake(function(options) {
        options.success();
    });

    var callback = jasmine.createSpy();
    getTodo(15, callback);

    expect($.ajax.mostRecentCall.args[0]["url"]).toEqual("/todos/15");
    expect(callback).toHaveBeenCalled();
});

function getTodo(id, callback) {
    $.ajax({
        type: "GET",
        url: "/todos/" + id,
        dataType: "json",
        success: callback
    });
}
```

```andCallFake()```��```toHaveBeenCalled()```��ƥ�䷽��������Spy���õ�ƥ�䷽�����Կ�Jasmine [wiki](https://github.com/pivotal/jasmine/wiki/Spies)��

�ڶ��ֲ���(�첽����)�����ǿ�����Jasmine֧�ֵ�����������������ǰ���������Щ�Ľ���

* runs(function) - ��������һ�������
* waits(timeout) - ��һ�������ִ��ǰ�ȴ�һ��ʱ��
* waitsFor(function, optional message, optional timeout)������ͣspecs֪��ĳЩ������ɡ�Jasmine��ȴ������ṩ�ĺ�������trueȻ���ټ���ִ����һ����롣


```javascript
it("should make an actual AJAX request to a server", function () {

    var callback = jasmine.createSpy();
    getTodo(16, callback);

    waitsFor(function() {
        return callback.callCount > 0;
    });

    runs(function() {
        expect(callback).toHaveBeenCalled();
    });
});

function getTodo(id, callback) {
    $.ajax({
        type: "GET",
        url: "todos.json",
        dataType: "json",
        success: callback
    });
}
```

***��ʾ��*** ���ڵ�Ԫ�����д�����ʵ�ķ�����������ʱ���Ἣ��������������е��ٶ�(�кܶ����أ������������ӳ�)��ͬʱҲ�������ⲿ������ԭ������(ҲӦ��Ҫ)��С����ĵ�Ԫ���ԣ�����ǿ���Ƽ���ѡ��spies������ʹ����ʵ�ķ������˵��á�

## beforeEach() and afterEach()

Jasmineͬ��֧����ÿ������֮ǰ(```beforeEach()```)����֮��(```afterEach```)ִ���ض��Ĵ��롣���ǿ��Ϊһ�µ������ǳ�����(��������specs����ı���)��������������У�```beforeEach()```�д���һ��specs���ڲ������Ե�Todo model��

```javascript
beforeEach(function(){
   this.todo = new Backbone.Model({
      text: 'Buy some more groceries',
      done: false
   });
});

it('should contain a text value if not the default value', function(){
   expect(this.todo.get('text')).toEqual('Buy some more groceries');
});
```

ÿ��```describe()```�ж���Ƕ���Լ���```beforeEach()```��```afterEach()```������֧�ֶ�Ӧsuite��ص�setup��teardown������




`beforeEach()` and `afterEach()` can be used together to write tests verifying that our Backbone routes are being correctly triggered when we navigate to the URL. We can start with the `index` action:

```javascript
describe('Todo routes', function(){

   beforeEach(function(){

        // Create a new router
        this.router = new App.TodoRouter();

        // Create a new spy
        this.routerSpy = jasmine.spy();

        // Begin monitoring hashchange events
        try{
            Backbone.history.start({
                silent:true,
                pushState: true
            });
        }catch(e){
           // ...
        }

        // Navigate to a URL
        this.router.navigate('/js/spec/SpecRunner.html');
   }); 

   afterEach(function(){

        // Navigate back to the URL
        this.router.navigate('/js/spec/SpecRunner.html');

        // Disable Backbone.history temporarily.
        // Note that this is not really useful in real apps but is
        // good for testing routers
        Backbone.history.stop();
   });

   it('should call the index route correctly', function(){
        this.router.bind('route:index', this.routerSpy, this);
        this.router.navigate('', {trigger: true});

        // If everything in our beforeEach() and afterEach()
        // calls have been correctly executed, the following
        // should now pass.
        expect(this.routerSpy).toHaveBeenCalledOnce();
        expect(this.routerSpy).toHaveBeenCalledWith();
   });

});
```

The actual TodoRouter for that would make the above test pass looks like:

```javascript
var App = App || {};
App.TodoRouter = Backbone.Router.extend({
    routes:{
        '': 'index'
    },
    index: function(){
        //...
    }
});
```

## Shared scope

Let's imagine we have a Suite where we wish to check for the existence of a new Todo item instance. This could be done by duplicating the spec as follows:

```javascript
describe("Todo tests", function(){
   
   // Spec
   it("Should be defined when we create it", function(){
        // A Todo item we are testing
        var todo = new Todo("Get the milk", "Tuesday");
        expect(todo).toBeDefined();
   }); 

   it("Should have the correct title", function(){
        // Where we introduce code duplication
        var todo = new Todo("Get the milk", "Tuesday");
        expect(todo.title).toBe("Get the milk");
   });

});
```

As you can see, we've introduced duplication that should ideally be refactored into something cleaner. We can do this using Jasmine's Suite (Shared) Functional Scope.

All of the specs within the same Suite share the same functional scope, meaning that variables declared within the Suite itself are available to all of the Specs in that suite. This gives us a way to work around our duplication problem by moving the creation of our Todo objects into the common functional scope:

```javascript
describe("Todo tests", function(){
    
    // The instance of Todo, the object we wish to test
    // is now in the shared functional scope
    var todo = new Todo("Get the milk", "Tuesday");

    // Spec
    it("should be correctly defined", function(){
        expect(todo).toBeDefined();
    });

    it("should have the correct title", function(){
        expect(todo.title).toBe("Get the milk");
    });

});
```

ǰ�������ע�⵽```beforeEach()```���������Ƕ�����һ������```this.todo```��Ȼ����```afterEach()```Ҳ���Լ���ʹ��������Ҫ�鹦��Jasmine�Ĺ������򡣹�������������п�(����```runs()```)���ʵ�```this```�����Զ�����ͬ�ģ����������ı���֮��(```var```�����ı���)��

##��ȡ��װ

���������������»���ԭ��������Jasmine�������ñ�д����ǰ��׼����

�ٷ������汾���Դ�����[����](https://github.com/pivotal/jasmine/downloads)��

���ص��İ��л���һ��SpecRunner.html�ļ��� Jasmine����ֿ���Դ���git�������ȡhttps://github.com/pivotal/jasmine.git��

����������SpecRunner.html�ļ�(����ʾ���������������°汾��Jasmine������)��

��������Jasmine�ͱ�Ҫ����report��css��


	<link rel="stylesheet" type="text/css" href="lib/jasmine-1.1.0.rc1/jasmine.css"/>
	<script type="text/javascript" src="lib/jasmine-1.1.0.rc1/jasmine.js"></script>
	<script type="text/javascript" src="lib/jasmine-1.1.0.rc1/jasmine-html.js"></script>


Ȼ������һЩ���ԣ�


	<script type="text/javascript" src="spec/SpecHelper.js"></script>
	<script type="text/javascript" src="spec/PlayerSpec.js"></script>


�������Ҫ�����ԵĴ��룺


	<script type="text/javascript" src="src/Player.js"></script>
	<script type="text/javascript" src="src/Song.js"></script>


***��ʾ��*** SpecRunner����Ĵ����Ǹ������в��ԡ� ���ﲻ�������������㿴��PlayerSpec.js��SpecHelper.js�Ĵ��롣���Ǹ������һ����Եĺܺõ����ӡ�

##TDD With Backbone

��ʹ��Backbone����Ӧ��ʱ����Ҫ���Ը����ģ�����ͬʱҲҪ����models, views, collections��routers������TDD���Է��������������²���Backbone [Todo](https://github.com/addyosmani/todomvc/tree/gh-pages/architecture-examples/backbone)���ʾ����Ŀ��Backbone�����һЩspecs����һ�����ǽ�ʹ��һ����Larry Myers�޸İ汾��Backbone Koans��Ŀ�� ��`practicals\jasmine-koans`Ŀ¼�¡�

## Models

Backbone models�ĸ��ӳ̶���ȫ������Ӧ��Ҫʵ�ֵĹ��ܡ����������У����ǽ�����Ĭ��ֵ�����ԣ�״̬�ı䣬����֤����

���ȣ�ʹ��```describe()```����suite��

```javascript
describe('Tests for Todo', function() {
```

Model������������Ӧ����Ĭ��ֵ������ȷ������ʵ��ʱδָ��ֵ�Ļ�����ʹ��Ĭ��ֵ������������˼��Ҫ����models�����ǿ��Ա���һЩ�������Ϊ��

�������spec������һ��Todoû�д����κ����ԣ�Ȼ������```text```���Ե�ֵ��ʲô����Ϊû�������κ�ֵ����������������ֵ�Ƿ���```""```��

```javascript
it('Can be created with default values for its attributes.', function() {
    var todo = new Todo();
    expect(todo.get('text')).toBe("");
});
```

������ڱ�дmodelǰ�������spec�Ļ���������ʧ�ܡ����spec��Ҫ����һ��```text```���Ե�Ĭ��ֵ��ʾ����

```javascript

window.Todo = Backbone.Model.extend({

    defaults: {
      text: "",
      done:  false,
      order: 0
    }

```

�����������ǲ�����model�ڳ�ʼ��֮��������ֵ��Ϊ�����ֵ������Ҳ�����������������Ե�Ĭ��ֵ�Ƿ������������ġ�

```javascript
it('Will set passed attributes on the model instance when created.', function() {
    var todo = new Todo({ text: 'Get oil change for car.' });

    // what are the values expected here for each of the
    // attributes in our Todo?

    expect(todo.get('text')).toBe("Get oil change for car.");
    expect(todo.get('done')).toBe(false);
    expect(todo.get('order')).toBe(0);
});
```
Backbone models֧��model.change()�¼�����model��״̬�ı�ʱ������������������У�ͨ������Todo model����ֵ���ı�����'state(״̬)'��״̬�ı��ԭ��ǳ�ֵ�ò��ԣ���ΪӦ���п�����״̬�������¼������統model���޸�ʱ��Ҫ��ʾһ��ȷ����ͼ��

```javascript
it('Fires a custom event when the state changes.', function() {

    var spy = jasmine.createSpy('-change event callback-');

    var todo = new Todo();

    // how do we monitor changes of state?
    todo.on('change', spy);

    // what would you need to do to force a change of state?
    todo.set({ text: 'Get oil change for car.' });

    expect(spy).toHaveBeenCalled();
});
```

ͨ����model��������֤�߼���ȷ�������û�������(��������ģ��)����Ч��'(valid)'��Todo app���ܻ���֤text������������������û�д�³�ĵ��ʡ� ͬ���ģ�
������Todo��```done```״̬ʱ����Ҫ��֤�����ֵ��true/false�� �������ַ�����

�������spec�У���������һЩ����֤ʧ�ܵ�ֵ����model.validate()����"error"�¼�������һ�´�����Чֵ���Ƿ����Ĵ���ʧ�ܡ�

ʹ��Jasmine����```createSpy()```��������һ��errorCallback spy���Ϳ��Լ��error�¼��ˣ�

```javascript
it('Can contain custom validation rules, and will trigger an error event on failed validation.', function() {

    var errorCallback = jasmine.createSpy('-error event callback-');

    var todo = new Todo();

    todo.on('error', errorCallback);

    // What would you need to set on the todo properties to
    // cause validation to fail?

    todo.set({done:'a non-integer value'});

    var errorArgs = errorCallback.mostRecentCall.args;

    expect(errorArgs).toBeDefined();
    expect(errorArgs[0]).toBe(todo);
    expect(errorArgs[1]).toBe('Todo.done must be a boolean value.');
});

```
Ҫ���������ʧ�ܲ��Դ���֧����֤�ǳ��򵥡����model�У�������дvalidate()����(��Backbone�ĵ��Ƽ�������)�����model��'done'���Բ��Ҹ�������ֵʱ��һ���Ϸ��Ĳ���ֵ��

```javascript
validate: function(attrs) {
    if (attrs.hasOwnProperty('done') && !_.isBoolean(attrs.done)) {
        return 'Todo.done must be a boolean value.';
    }
}
```

���������Todo model�������£�

```javascript
var NAUGHTY_WORDS = /crap|poop|hell|frogs/gi;

function sanitize(str) {
    return str.replace(NAUGHTY_WORDS, 'rainbows');
}

window.Todo = Backbone.Model.extend({

    defaults: {
      text: '',
      done:  false,
      order: 0
    },

    initialize: function() {
        this.set({text: sanitize(this.get('text'))}, {silent: true});
    },

    validate: function(attrs) {
        if (attrs.hasOwnProperty('done') && !_.isBoolean(attrs.done)) {
            return 'Todo.done must be a boolean value.';
        }
    },

    toggle: function() {
        this.save({done: !this.get("done")});
    }

});
```


## Collections

����������Ҫ����specs������Backbone Todo model��collection(һ��TodoList)��Collections�����б�����򣬹��˵ȡ�

����collectionsʱ���ܻ���������Щ��ȷ��specs��

* ��������µ�Todo model������߶�������顣
* ���Բ��ԣ�ȷ������collection��base URL������������ֵ��
* ��������״̬```done:true```��todo� Ȼ����collection��Ϊ��������������δ������������

��һ������ֻ�ὲ��ǰ2�����⣬������������Ϊ���ߵ�������ϰ��

����Todo models��ͨ��һ��������������������Լ򵥡����ȣ���ʼ��һ��TodoList collection��ȷ���䳤��Ϊ0��Ȼ������µ�Todos�����������������������һ�Σ�Ȼ����collection��length�����Ƿ��������ֵ��

```javascript
describe('Tests for TodoList', function() {

    it('Can add Model instances as objects and arrays.', function() {
        var todos = new TodoList();

        expect(todos.length).toBe(0);

        todos.add({ text: 'Clean the kitchen' });

        // how many todos have been added so far?
        expect(todos.length).toBe(1);

        todos.add([
            { text: 'Do the laundry', done: true },
            { text: 'Go to the gym'}
        ]);

        // how many are there in total now?
        expect(todos.length).toBe(3);
    });
...
```

��model������һ��������collections������Ҳ�ǳ��򵥡�������һ���򵥵Ĳ���collection.url��spec���ӣ�

```javascript
it('Can have a url property to define the basic url structure for all contained models.', function() {
        var todos = new TodoList();

        // what has been specified as the url base in our model?
        expect(todos.url).toBe('/todos/');
});

```

���ڵ�����spec��collection��ʵ��``done()```��```remaining()```�������ֱ���������Todo���δ������дһ��spec������һ��collection�����һ��```done```״̬ΪΪ```true```��model��2��```done```״̬Ϊ```false```��model��Ȼ����Ե���```done()```��```remaining()```�������صĽ����length�����Ƿ�������

TodoList collectionʵ�ִ������������������


```javascript
 window.TodoList = Backbone.Collection.extend({

        model: Todo,

        url: '/todos/',

        done: function() {
            return this.filter(function(todo) { return todo.get('done'); });
        },

        remaining: function() {
            return this.without.apply(this, this.done());
        },

        nextOrder: function() {
            if (!this.length) {
                return 1;
            }

            return this.last().get('order') + 1;
        },

        comparator: function(todo) {
            return todo.get('order');
        }

    });
```


## Views

�ڿ�ʼ����Backbone viewsǰ���ȼ�̵�����һ����дJasmine specs��jQuery plugin��

**The Jasmine jQuery Plugin**

Todo applicationʹ��jQuery����DOM��������һ��[jasmine-jquery](https://github.com/velesin/jasmine-jquery) ������԰�����BDD����view������Ԫ�ء�


�������ṩ�˺ܶ�����Jasmine [matchers](https://github.com/pivotal/jasmine/wiki/Matchers) �԰�������jQuery��װ��sets��

* ```toBe(jQuerySelector)```ʾ�� �� ```expect($('<div id="some-id"></div>')).toBe('div#some-id')```
* ```toBeChecked()``` ʾ����```expect($('<input type="checkbox" checked="checked"/>')).toBeChecked()```
* ```toBeSelected()``` ʾ�� ```expect($('<option selected="selected"></option>')).toBeSelected()```

������Բο� [����](https://github.com/velesin/jasmine-jquery)����֧�ֵ�����matchers��������Ŀ��ҳ���ҵ���������׼��Jasmine matchers���ƣ������matchers���Լ�.notǰ׺������ʹ��(����```expect(x).not.toBe(y)```)��

```javascript
expect($('<div>I am an example</div>')).not.toHaveText(/other/)
```

jasmine-jqueryͬʱ����һ���̶�װ��ģ��(fixtures model)�����Լ�������HTML���ݵ�ʱ�򡣿�������������ʹ�ã�

��һ���ⲿ�ļ��а���һ��HTML��

some.fixture.html:
```<div id="sample-fixture">some HTML content</div>```

Ȼ��ʵ�ʲ���ʱ�������������룺

```javascript
loadFixtures('some.fixture.html')
$('some-fixture').myTestedPlugin();
expect($('#some-fixture')).to<the rest of your matcher would go here>
```

jasmine-jquery���Ĭ�ϻ��һ���ض�Ŀ¼����fixtures��spec/javascripts/fixtures��������������·���Ļ��ڳ�ʼ��������```jasmine.getFixtures().fixturesPath = 'your custom path'```��

���jasmine-jquery������jQuery�¼�spying��֧�֣����Ҳ���Ҫʲô����Ĺ�������ʹ��```spyOnEvent()```��```assert(eventName).toHaveBeenTriggered(selector)```��������ɡ�������һ��ʾ����

```javascript
spyOnEvent($('#el'), 'click');
$('#el').click();
expect('click').toHaveBeenTriggeredOn($('#el'));
```


### View����

��һС�����Ǵ�����ά�������±�дBackbone Views��specs����ʼ����view��Ⱦ��ģ�����ɡ���������ͨ���Ĳ��Բ�࣬�����һ��̵�˵��Ϊʲô��views�ĳ�ʼ����дspecsҲ���кô��ġ�

#### ��ʼ��

������ģ�ΪBackbone viewsд��specs��Ҫ��֤view����ȷ�İ󶨵�ָ����DOMԪ�أ�����Ч������model֧�֡�������������ԭ���ǣ������Щspecsʧ�ܵĻ��ᵼ�º���һЩ�����ӵĲ���Ҳʧ�ܣ�������Щspecsд�����Ƚϼ򵥣������ṩһ������ļ�ֵ��

Ϊȷ��һ�µĲ�������������ʹ��```beforeEach()```׷��һ���յ�```UL``` (#todoList)��DOM������һ���յ�Todo model��ʼ��һ��TodoViewʵ������```afterEach()```���Ƴ�ǰ���#todoList  ```UL```��viewʵ����

```javascript
describe('Tests for TodoView', function() {

    beforeEach(function() {
        $('body').append('<ul id="todoList"></ul>');
        this.todoView = new TodoView({ model: new Todo() });
    });


    afterEach(function() {
        this.todoView.remove();
        $('#todoList').remove();
    });

...
```

��һ��spec���Ǽ�����Ǵ�����TodoViewʹ������ȷ��```tagName```(Ԫ�ػ���className)��Ŀ�ľ���ȷ������ʱ��ȷ�İ󶨵�DOMԪ�ء�

Backbone viewsͨ��һ����ʼ���ᴴ��һЩ�յ�DOMԪ�أ�������ЩԪ�ز��ḽ�ӵ��ɼ���DOM�У� Ŀ�����ڲ�Ӱ�����ܺ���Ⱦ������������ǹ���������

```javascript
it('Should be tied to a DOM element when created, based off the property provided.', function() {
    //what html element tag name represents this view?
    expect(todoView.el.tagName.toLowerCase()).toBe('li');
});
```

���TodoView��û��д�õĻ���specs�ͻ�ʧ�ܡ�ͨ��ָ��```tagName```����һ��Backbone.View��

```javascript
var todoView = Backbone.View.extend({
    tagName:  "li"
});
```

Ҳ����ͨ������className�����```tagName```������ʹ�ø��߼���jasmine-jquery matcher ```toHaveClass()```����ɡ�

```
it('Should have a class of "todos"'), function(){
   expect(this.view.$el).toHaveClass('todos');
});
```

```toHaveClass()``` matcher��jQuery�������������û��ʹ���������Ļ��ͻ������쳣(���û��ʹ��jasmine-jquery���Ҳ��ͨ����ȡel.className���ж�)��

�����ע�⵽```beforeEach()```�����Ǵ�����һ���´�����Todo��view��ViewsӦ�û���һ�������ݵ�modelʵ������Ϊ����view�Ĺ��ܷǳ���Ҫ�����ǿ���дһ��spec��ȷ��model��һ����(ʹ��```toBeDefined()``` matcher) ���Ҳ���model��Ĭ�����ԣ�����������������ֵ��

```javascript
it('Is backed by a model instance, which provides the data.', function() {

    expect(todoView.model).toBeDefined();

    // what's the value for Todo.get('done') here?
    expect(todoView.model.get('done')).toBe(false); //or toBeFalsy()
});
```


#### View��Ⱦ


���������¸�view��Ⱦ��дspecs���ر��ǣ������������TodoViewʵ�ʱ���Ⱦ������Ԫ���Ƿ����������

����С�Ķ�applications����ЩBDD������Ϊ�Ӿ���ȷ��view����Ⱦ�������view�ĵ�Ԫ���ԡ�ʵ���ϣ�������Ӧ�ÿ��ܱ�ɶ��Ӹ�viewʱ��ͨ���ӿ��˾;�������������Զ�����ͬ��Ҳ��aspects����֤��Ļ������������ȾЧ����

���Ǳ�д����spec������view����һ�����Լ쳵view��```render()```������ȷ�ķ���viewʵ��������������ʽ���á��ڶ������Լ�����ɵ�HTML�ǻ���TodoView�������modeʵ���������������Ľ����

��ͬ��ǰ������д��specs����һ�����ǻ����ʹ��```beforeEach()```�������ʹ��Ƕ�׵�suites���Լ�ȷ��specs������һ�¡���һ��TodoView��spec��������һ���򵥵�model (����Todo)��Ȼ�������model��ʼ��һ��TodoView��

```javascript
describe("TodoView", function() {

  beforeEach(function() {
    this.model = new Backbone.Model({
      text: "My Todo",
      order: 1,
      done: false
    });
    this.view = new TodoView({model:this.model});
  });

  describe("Rendering", function() {

    it("returns the view object", function() {
      expect(this.view.render()).toEqual(this.view);
    });

    it("produces the correct HTML", function() {
      this.view.render();

      //let's use jasmine-jquery's toContain() to avoid
      //testing for the complete content of a todo's markup
      expect(this.view.el.innerHTML)
        .toContain('<label class="todo-content">My Todo</label>');
    });

  });

});
```

��Щspecsһ�����У�ֻ�еڶ���('produces the correct HTML')ʧ�ܡ���һ��spec ('returns the view object')������```render()```���ص�TodoViewʵ���� ����ͨ����Ϊ����Backbone��Ĭ����Ϊ�����ǲ�û����д```render()```������

**��ʾ��** Ϊ��ά���ɶ��ԣ���һ�������е�ģ�����Ӷ���ʹ�����������С���汾��Todo viewģ�塣��Ҫʹ��ʱ���Է������鿴��

	<div class="todo <%= done ? 'done' : '' %>">
	        <div class="display">
	          <input class="check" type="checkbox" <%= done ? 'checked="checked"' : '' %> />
	          <label class="todo-content"><%= text %></label>
	          <span class="todo-destroy"></span>
	        </div>
	        <div class="edit">
	          <input class="todo-input" type="text" value="<%= content %>" />
	        </div>
	</div>



�ڶ���specʧ�ܻ������������ʾ��

```Expected '' to contain '<label class="todo-content">My Todo</label>'.```

ԭ����render()��Ĭ����Ϊ�������κα�ǩ����������дһ�������render()���������

```javascript
render: function() {
  var template = '<label class="todo-content"><%= text %></label>';
  var output = template
    .replace("<%= text %>", this.model.get('text'));
  this.$el.html(output);
  return this;
}
```

����ָ����һ��ģ���ַ�����Ȼ����model��Ӧ������ֵ�滻"<% %>"�����ڵ����ݡ�ͬʱҲ����TodoViewʵ�������Ե�һ��specҲ����ͨ������������spec��ʹ��HTML�ַ��������в����зǳ����ȱ�㡣������ģ��΢С�ı仯(һ��tab���߿ո��)�ͻᵼ��specʧ�ܣ�������Ⱦ�����һ���ġ�ʵ��Ӧ����ģ��Ҳ������ӣ����ķѸ����ʱ��ȥά�������õĲ�����Ⱦ�������ķ�����ʹ��jQuery��ѡ��ͼ�顣

�������˼�룬��������д���spec��ʹ��jasmine-jquery�ṩ���Զ���matchers��


```javascript
describe("Template", function() {

  beforeEach(function() {
    this.view.render();
  });

  it("has the correct text content", function() {
    expect(this.view.$('.todo-content'))
      .toHaveText('My Todo');
  });

});
```

���۵�Ԫ���Բ��ᵽfixtures�ǲ����ܵġ�Fixturesͨ��������Ԫ���Ե���Ҫʱ(�����Ǳ��ػ��ߴ��ⲿ�ļ�)����Ĳ�������(����HTML)�� һֱ�������Ƕ��ǰ�jQuery������������view��el�����ϡ��󲿷����������Ч�ģ���������ʱ������Ҫ�ѱ�ǩ��Ⱦ��document����specs�д����������������뷽ʽ����ʹ��fixtures (jasmine-jquery����������ǵ�����һ������)��

ʹ��fixtures��д�������spec��


```javascript
describe("TodoView", function() {

  beforeEach(function() {
    ...
    setFixtures('<ul class="todos"></ul>');
  });

  ...

  describe("Template", function() {

    beforeEach(function() {
      $('.todos').append(this.view.render().el);
    });

    it("has the correct text content", function() {
      expect($('.todos').find('.todo-content'))
        .toHaveText('My Todo');
    });

  });

});
```

���������spec�У�����Ⱦ��todoԪ��append��fixture��Ȼ������fixture������������view��Ӧ��һ���Ѿ����ڵ�DOMԪ��֮���һЩdesirable���б�Ҫ�ṩfixture�Ͳ��Ե�view��ʼ����ʱ��```el```�����Ƿ�ָ����ȷ��Ԫ�ء�


#### ʹ��ģ��ϵͳ������Ⱦ


��һ���û�����һ��Tood��Ϊ���(done)�ǣ�������������һ���Ӿ��ϵķ���(�����ı��ϼ�һ������)����������ĵ������ͨ����������һ��class��ʵ�֡����濪ʼ��д���ԣ�


```javascript
describe('When a todo is done', function() {

  beforeEach(function() {
    this.model.set({done: true}, {silent: true});
    $('.todos').append(this.view.render().el);
  });

  it('has a done class', function() {
    expect($('.todos .todo-content:first-child'))
      .toHaveClass('done');
  });

});
```

������ʧ�ܣ�������������Ϣ��

```Expected '<label class="todo-content">My Todo</label>'
to have class 'done'.
```


������render()�����н����


```javascript
render: function() {
  var template = '<label class="todo-content">' +
    '<%= text %></label>';
  var output = template
    .replace('<%= text %>', this.model.get('text'));
  this.$el.html(output);
  if (this.model.get('done')) {
    this.$('.todo-content').addClass('done');
  }
  return this;
}
```

�������ܿ����ͻ��ò���ô�����ˡ�����ģ�����߼������ӣ����ͻ���Խ���ӡ����ǿ���ͨ��ʹ��ģ������׵Ľ��������⡣�����ģ���Ҳ�ܺܺõ�����Է���һ����ϵĺܺã�����Jasmine��

JavaScriptģ��ϵͳ(����Handlebars, Mustache �Լ�Underscore��Micro-templating)��ģ���ַ�����֧�������߼��������ζ�����ǿ���һ���ַ�����ʹ��if/else/��Ԫ��ʱ�����Թ�����ǿ���ģ�塣

�����ǵİ����У���������ѡ��Underscore���õ�Microtemplating������Ҫ��Ӷ�����ļ������Ҷ�����specsҲ����Ҫ��̫����޸ġ�

����ģ�嶨����ID `myTemplate`��script��ǩ��:

```
<script type="text/template" id="myTemplate">
    <div class="todo <%= done ? 'done' : '' %>">
            <div class="display">
              <input class="check" type="checkbox" <%= done ? 'checked="checked"' : '' %> />
              <label class="todo-content"><%= text %></label>
              <span class="todo-destroy"></span>
            </div>
            <div class="edit">
              <input class="todo-input" type="text" value="<%= content %>" />
            </div>
    </div>
</script>
```

TodoView����ʹ��Underscoreģ���޸ĳ���������:

```javascript
var TodoView = Backbone.View.extend({

  tagName: 'li',
  template: _.template($('#myTemplate').html()),

  initialize: function(options) {
    // ...
  },

  render: function() {
    this.$el.html(this.template(this.model.toJSON()));
    return this;
  },

  ...

});
```

So, what's going on here? We're first defining our template in a script tag with a custom script type (e.g., type="text/template"). As this isn't a script type any browser understands, it's simply ignored, however referencing the script by an id attribute allows the template to be kept separate to other parts of the page.

In our view, we're the using the Underscore `_.template()` method to compile our template into a function that we can easily pass model data to later on. In the line `this.model.toJSON()` we are simply returning a copy of the model's attributes for JSON stringification to the `template` method, creating a block of HTML that can now be appended to the DOM.

Note: Ideally all of your template logic should exist outside of your specs, either in individual template files or embedded using script tags within your SpecRunner. This is generally more maintainable.

If you are working with much smaller templates and are not doing this, there is however a useful trick that can be applied to automatically create or extend templates in the Jasmine shared functional scope for each test. 

By creating a new directory (say, 'templates') in the 'spec' folder and including a new script file with the following contents into SpecRunner.html, we can manually add custom attributes representing smaller templates we wish to use:

```javascript
beforeEach(function() {
  this.templates = _.extend(this.templates || {}, {
    todo: '<label class="todo-content">' +
            '<%= text %>' +
          '</label>'
  });
});
```

To finish this off, we simply update our existing spec to reference the template when instantiating the TodoView:

```javascript
describe('TodoView', function() {

  beforeEach(function() {
    ...
    this.view = new TodoView({
      model: this.model,
      template: this.templates.todo
    });
  });

  ...

});
```

The existing specs we've looked at would continue to pass using this approach, leaving us free to adjust the template with some additional conditional logic for Todos with a status of 'done':

```javascript
beforeEach(function() {
  this.templates = _.extend(this.templates || {}, {
    todo: '<label class="todo-content <%= done ? 'done' : '' %>"' +
            '<%= text %>' +
          '</label>'
  });
});
```

This will now also pass without any issues, however as mentioned, this last approach probably only makes sense if you're working with smaller, highly dynamic templates. 


## �ܽ�

���������Ѿ��������ΪBackbone.jsӦ���е�models, views��collections��дJasmine���ԡ���Ȼ����·��(routing)��ʱ�ǿ�ȡ�ģ���Щ��������Ϊ�������ɵ��������߸��õ���ɱ���Selenium���������ס��㡣

## ��ϰ

A��Ϊ��ϰ���Ƽ���ҳ�����Jasmine Koans����`practicals\jasmine-joans`Ŀ¼�£�Ȼ����fixһЩ���������ṩ��ʧ�ܵĲ��ԡ�����һ�ֺܺõ��˽�Jasmine specs �� suites����ԭ���ѧϰBackbone���ɵķ�ʽ��


## ��չ�Ķ�
* [Testing Backbone Apps With SinonJS](http://tinnedfruit.com/2011/04/26/testing-backbone-apps-with-jasmine-sinon-3.html) by James Newbry
* [Jasmine + Backbone Revisited](http://japhr.blogspot.com/2011/11/jasmine-backbonejs-revisited.html)
* [Backbone, PhantomJS and Jasmine](http://japhr.blogspot.com/2011/12/phantomjs-and-backbonejs-and-requirejs.html)
