#SinonJS

��ǰ��ʹ��Jasmine BDD��ܲ���Backbone.js app���ƣ�����ͨ����TodoӦ��дһЩQUnit������ѧϰ��

�����ע�⵽QUnit��֧��spies��Test spies��¼�������쳣���ҷ���ֵ�������ĵ��á�ͨ�����ڲ��Իص����Լ�������α�ʹ�á��ڲ��Կ���У�spies����������Ҳ�����ǰ������еĺ�����


##ʲô��SinonJS?

��QUnit�����ǿ�����Christian Johansen��д��ģ����[SinonJS](http://sinonjs.org/)��֧��spies��ͬʱ��Ҫʹ��[SinonJS-QUnit adapter](http://sinonjs.org/qunit/)����QUnit�����޷켯�ɡ�Sinon.JS ����ȫ����Կ���޹صģ����ҿ������׵����κβ��Կ��һͬʹ�ã����Զ������ǵ��������Ƿǳ������ѡ��

������֧�������������ǻ��ڵ�Ԫ���������ϣ�

* **����spies**
* **���(Spying on)���еķ���**
* **�ḻ�ļ��ӽӿ�**

ʹ��```this.spy()```�������κβ����򴴽�һ��������spy��������```jasmine.createSpy()```���Ƚϣ� �����ǻ�����ʹ��SinonJS spy�����ӣ�

####Basic Spies:
```javascript
test("should call all subscribers for a message exactly once", function () {
    var message = getUniqueString();
    var spy = this.spy();

    PubSub.subscribe( message, spy );
    PubSub.publishSync( message, "Hello World" );

    ok( spy1.calledOnce, "the subscriber was called once" );
});
```

ͬ������ʹ��```this.spy()```�������������������еĺ���(����jQuery��```$.ajax```)����������һ�����к���ʱ�����ĺ�����Ϊ���������һ�����������ǿ��Է��ʵ����õ�����������ڲ��ԡ�

####Spying On Existing Functions:
```javascript
test( "should inspect jQuery.getJSON's usage of jQuery.ajax", function () {
    this.spy( jQuery, "ajax" );

    jQuery.getJSON( "/todos/completed" );

    ok( jQuery.ajax.calledOnce );
    equals( jQuery.ajax.getCall(0).args[0].url, "/todos/completed" );
    equals( jQuery.ajax.getCall(0).args[0].dataType, "json" );
});
```

SinonJS�ṩ��һ�׷ḻ�ļ��ӽӿڣ����Բ���һ��spy�Ƿ�ʹ��ָ���Ĳ������ã��Ƿ񱻵�����ָ���Ĵ������Լ����Ե���ʱ������ֵ���ӿ�֧�ֵ��������Կ��Կ�����(http://sinonjs.org/docs/)������ͨ��һЩ���������³��õ����ԣ�


####����ƥ�䣺����һ��spy�Ƿ�ʹ��ָ���������ã�

```javascript
test( "Should call a subscriber with standard matching": function () {
    var spy = sinon.spy();

    PubSub.subscribe( "message", spy );
    PubSub.publishSync( "message", { id: 45 } );

    assertTrue( spy.calledWith( { id: 45 } ) );
});
```

####�ϸ�Ĳ���ƥ�䣺����һ��spyʹ��ָ���Ĳ����������������������ٱ�����һ�Σ� 

```javascript
test( "Should call a subscriber with strict matching": function () {
    var spy = sinon.spy();

    PubSub.subscribe( "message", spy );
    PubSub.publishSync( "message", "many", "arguments" );
    PubSub.publishSync( "message", 12, 34 );

    // This passes
    assertTrue( spy.calledWith("many") );

    // This however, fails
    assertTrue( spy.calledWithExactly( "many" ) );
});
```

####���Ե���˳�򣺲���һ��spy�Ƿ�����һ��spy֮ǰ��֮����ã�

```javascript
test( "Should call a subscriber and maintain call order": function () {
    var a = sinon.spy();
    var b = sinon.spy();

    PubSub.subscribe( "message", a );
    PubSub.subscribe( "event", b );

    PubSub.publishSync( "message", { id: 45 } );
    PubSub.publishSync( "event", [1, 2, 3] );

    assertTrue( a.calledBefore(b) );
    assertTrue( b.calledAfter(a) );
});
```

####ƥ��ִ�д���������һ���Ƿ񱻵�����ָ���Ĵ�����

```javascript
test( "Should call a subscriber and check call counts", function () {
    var message = getUniqueString();
    var spy = this.spy();

    PubSub.subscribe( message, spy );
    PubSub.publishSync( message, "some payload" );


    // Passes if spy was called once and only once.
    ok( spy.calledOnce ); // calledTwice and calledThrice are also supported

    // The number of recorded calls.
    equal( spy.callCount, 1 );

    // Directly checking the arguments of the call
    equals( spy.getCall(0).args[0], message );
});
```


##Stubs��mocks

SinonJS��֧������2��ǿ������ԣ�stubs��mocks��stubs��mocks��ʵ����spy API���������ԣ��������д�������ܡ�

###Stubs

һ��stub�����������ǰ�ָ���ķ�������Ϊ�滻�������Ķ���������������ģ���쳣�������ڱ�д����Ҫ��������뻹û��дʱ�Ĳ��ԡ�

�������»ص�Backbone Todo application������һ��Todo model��һ��TodoList collection����Ϊ��ʾ�����ǰ�TodoList collection�������룬����Todo model����������µ�models�ᷢ��ʲô��

����models��û�б�д�ã���ʾ��stubbing��ν��С�һ������model���õ�collection��ǣ�

```javascript
var TodoList = Backbone.Collection.extend({
    model: Todo
});

// Let's assume our instance of this collection is
this.todoList;
```

����collection�������ʵ����models��������ҪΪ�������stub models�Ĺ��캯��������������������

```javascript
this.todoStub = sinon.stub( window, "Todo" );
```

������window�ϴ�����һ��Todo������stub����stubbingһ���־ö���ʱ�����ܻ���Ҫ�ָ���ԭʼ״̬������ʹ��```teardown()``` ��

```javascript
this.todoStub.restore();
```

Ȼ��������Ҫ�ı�������캯���ķ��أ�ʹ����ʵ��```Backbone.Model```����������Ȼ������һ��Todo model�������������ṩ��һ��ʵ�ʵ�Backbone model��


```javascript
teardown: function() {
    this.model = new Backbone.Model({
      id: 2,
      title: "Hello world"
    });
    this.todoStub.returns( this.model );
});
```

�����������������δ������ȷ��TodoList collection����ʵ����stubbed Todo model������collection�Ѿ�����һ��model�����ã�������Ҫ����������collection��model���ԣ�

```javascript
this.todoList.model = Todo;
```

�������Ľ�����ǣ���TodoList collectionʵ�����µ�Todo modelsʱ�����᷵�ظ�����һ��������Backbone model�������дһ��spec��������������model��

```javascript
module( "Should function when instantiated with model literals", {

  setup:function() {

    this.todoStub = sinon.stub(window, "Todo");
    this.model = new Backbone.Model({
      id: 2,
      title: "Hello world"
    });

    this.todoStub.returns(this.model);
    this.todos = new TodoList();

    // Let's reset the relationship to use a stub
    this.todos.model = Todo;
    this.todos.add({
      id: 2,
      title: "Hello world"
    });
  },

  teardown: function() {
    this.todoStub.restore();
  }

});

test("should add a model", function() {
    equal( this.todos.length, 1 );
});

test("should find a model by id", function() {
    equal( this.todos.get(5).get("id"), 5 );
  });
});
```


###Mocks

Mocksʵ���ϸ�stubsһ�����������ǻ�ģ�³�������API�������ʹ��������һЩ���õ������� mockҲspy�����������Ϊ����ʹ�õ�expectations��Ԥ����ģ�������κβ����ͻ�ʧ�ܡ�

���и�����PubSubJSʹ��mock�����ӡ���һ��`clearTodo()` ������Ϊ�ص���ʹ��mocks��У��������Ϊ��
```javascript
test("should call all subscribers when exceptions", function () {
    var myAPI = { clearTodo: function () {} };

    var spy = this.spy();
    var mock = this.mock( myAPI );
    mock.expects( "clearTodo" ).once().throws();

    PubSub.subscribe( "message", myAPI.clearTodo );
    PubSub.subscribe( "message", spy );
    PubSub.publishSync( "message", undefined );

    mock.verify();
    ok( spy.calledOnce );
});
```



��ϰ
====================

�������ǿ��Կ�ʼ��Todo applicationд����specs�ˣ��������(����Models, Collections��)���оٺͷָ�����Ҫע����Ե����ƣ������Ե��߼����Լ�����Ҫ�Ķ��ԣ���Щ������������ᵽ��ν���ѧ����Ӧ�õ�һ����������Ŀ�С�

���⣬�����㿴��`practicals\qunit-koans`Ŀ¼�µ�QUnit Koans - ������Ϊ��ƪ���½�Jasmine Koansת������QUnit��

*����㻹û�г��Թ�Koans kits������һ��ʹ���ض����Կ�ܵĵ�Ԫ���ԣ�չʾ�����Ϊһ��application��дһ��specs��ͬʱҲ����һЩû�����Ĳ�����Ϊ��ϰ��*

###Models

����model������Ҫ�������漸�㣺

* ����ʹ��������Ĭ��ֵ����ʵ��
* ���Կ������������úͻָ�
* ״̬�ĸı�����Ҫʱ������ȷ�Ĵ����Զ����¼�
* ��֤������ȷ��ִ��

```javascript
module( 'About Backbone.Model');

test('Can be created with default values for its attributes.', function() {
    expect( 1 );

    var todo = new Todo();

    equal( todo.get('text'), "" );
});

test('Will set attributes on the model instance when created.', function() {
    expect( 3 );

    var todo = new Todo( { text: 'Get oil change for car.' } );

    equal( todo.get('text'), "Get oil change for car." );
    equal( todo.get('done'), false );
    equal( todo.get('order'), 0 );
});

test('Will call a custom initialize function on the model instance when created.', function() {
    expect( 1 );

    var toot = new Todo({ text: 'Stop monkeys from throwing their own crap!' });
    equal( toot.get('text'), 'Stop monkeys from throwing their own rainbows!' );
});

test('Fires a custom event when the state changes.', function() {
    expect( 1 );

    var spy = this.spy();
    var todo = new Todo();

    todo.on( 'change', spy );
    // How would you update a property on the todo here?
    // Hint: http://documentcloud.github.com/backbone/#Model-set
    todo.set( { text: "new text" } );

    ok( spy.calledOnce, "A change event callback was correctly triggered" );
});


test('Can contain custom validation rules, and will trigger an error event on failed validation.', function() {
    expect( 3 );

    var errorCallback = this.spy();
    var todo = new Todo();

    todo.on('error', errorCallback);
    // What would you need to set on the todo properties to cause validation to fail?
    todo.set( { done: "not a boolean" } );

    ok( errorCallback.called, 'A failed validation correctly triggered an error' );
    notEqual( errorCallback.getCall(0), undefined );
    equal( errorCallback.getCall(0).args[1], 'Todo.done must be a boolean value.' );

});
```


###Collections

����collection����Ҫ���Ե����漸�㣺

* ��������µ�Todo model������߶�������顣
* models�ı仯�ᴥ����Ҫ���Զ����¼���
* ����models�ṹ��Ӧ��`url`��������ȷ�ġ�


```javascript
module( 'About Backbone.Collection');

test( 'Can add Model instances as objects and arrays.', function() {
    expect( 3 );

    var todos = new TodoList();
    equal( todos.length, 0 );

    todos.add( { text: 'Clean the kitchen' } );
    equal( todos.length, 1 );

    todos.add([
        { text: 'Do the laundry', done: true },
        { text: 'Go to the gym' }
    ]);

    equal( todos.length, 3 );
});

test( 'Can have a url property to define the basic url structure for all contained models.', function() {
    expect( 1 );
    var todos = new TodoList();
    equal( todos.url, '/todos/' );
});

test('Fires custom named events when the models change.', function() {
    expect(2);

    var todos = new TodoList();
    var addModelCallback = this.spy();
    var removeModelCallback = this.spy();

    todos.on( 'add', addModelCallback );
    todos.on( 'remove', removeModelCallback );

    // How would you get the 'add' event to trigger?
    todos.add( {text:"New todo"} );

    ok( addModelCallback.called );

    // How would you get the 'remove' callback to trigger?
    todos.remove( todos.last() );

    ok( removeModelCallback.called );
});
```



###Views

����views����Ҫȷ�����漸�㣺

* ����ʱ����ȷ�İ󶨵�DOMԪ�ء�
* view��ÿ��DOM�ɼ�֮�����Ⱦ��
* ֧��view������DOMԪ�ؼ�����ӡ�

Ҳ���Խ�һ������������view�Ľ�����Ϊ����ȷ����models��Ҫ�ĸ��¡�


```javascript
module( 'About Backbone.View', {
    setup: function() {
        $('body').append('<ul id="todoList"></ul>');
        this.todoView = new TodoView({ model: new Todo() });
    },
    teardown: function() {
        this.todoView.remove();
        $('#todoList').remove();
    }
});

test('Should be tied to a DOM element when created, based off the property provided.', function() {
    expect( 1 );
    equal( this.todoView.el.tagName.toLowerCase(), 'li' );
});

test('Is backed by a model instance, which provides the data.', function() {
    expect( 2 );
    notEqual( this.todoView.model, undefined );
    equal( this.todoView.model.get('done'), false );
});

test('Can render, after which the DOM representation of the view will be visible.', function() {
   this.todoView.render();

    // Hint: render() just builds the DOM representation of the view, but doesn't insert it into the DOM.
    //       How would you append it to the ul#todoList?
    //       How do you access the view's DOM representation?
    //
    // Hint: http://documentcloud.github.com/backbone/#View-el

    $('ul#todoList').append(this.todoView.el);
    equal($('#todoList').find('li').length, 1);
});

asyncTest('Can wire up view methods to DOM elements.', function() {
    expect( 2 );
    var viewElt;

    $('#todoList').append( this.todoView.render().el );

    setTimeout(function() {
        viewElt = $('#todoList li input.check').filter(':first');

        equal(viewElt.length > 0, true);

        // Make sure that QUnit knows we can continue
        start();
    }, 1000, 'Expected DOM Elt to exist');


    // Hint: How would you trigger the view, via a DOM Event, to toggle the 'done' status.
    //       (See todos.js line 70, where the events hash is defined.)
    //
    // Hint: http://api.jquery.com/click

    $('#todoList li input.check').click();
    expect( this.todoView.model.get('done'), true );
});
```

###Events

�����¼���������Ҫ��һЩ��һ���Ĳ���������

* ��չ������֧���Զ����¼�
* �󶨺ʹ���������Զ����¼�
* ���¼�����ʱ�ò��������ص�����
* ��һ������������İ󶨵�һ���¼��Ļص�
* �Ƴ��Զ����¼�

����һЩ����ϸ�ڽ��������ģ���У�

```javascript
module( 'About Backbone.Events', {
    setup: function() {
        this.obj = {};
        _.extend( this.obj, Backbone.Events );
        this.obj.off(); // remove all custom events before each spec is run.
    }
});

test('Can extend JavaScript objects to support custom events.', function() {
    expect(3);

    var basicObject = {};

    // How would you give basicObject these functions?
    // Hint: http://documentcloud.github.com/backbone/#Events
    _.extend( basicObject, Backbone.Events );

    equal( typeof basicObject.on, 'function' );
    equal( typeof basicObject.off, 'function' );
    equal( typeof basicObject.trigger, 'function' );
});

test('Allows us to bind and trigger custom named events on an object.', function() {
    expect( 1 );

    var callback = this.spy();

    this.obj.on( 'basic event', callback );
    this.obj.trigger( 'basic event' );

    // How would you cause the callback for this custom event to be called?
    ok( callback.called );
});

test('Also passes along any arguments to the callback when an event is triggered.', function() {
    expect( 1 );

    var passedArgs = [];

    this.obj.on('some event', function() {
        for (var i = 0; i < arguments.length; i++) {
            passedArgs.push( arguments[i] );
        }
    });

    this.obj.trigger( 'some event', 'arg1', 'arg2' );

    deepEqual( passedArgs, ['arg1', 'arg2'] );
});


test('Can also bind the passed context to the event callback.', function() {
    expect( 1 );

    var foo = { color: 'blue' };
    var changeColor = function() {
        this.color = 'red';
    };

    // How would you get 'this.color' to refer to 'foo' in the changeColor function?
    this.obj.on( 'an event', changeColor, foo );
    this.obj.trigger( 'an event' );

    equal( foo.color, 'red' );
});

test( "Uses 'all' as a special event name to capture all events bound to the object." , function() {
    expect( 2 );

    var callback = this.spy();

    this.obj.on( 'all', callback );
    this.obj.trigger( "custom event 1" );
    this.obj.trigger( "custom event 2" );

    equal( callback.callCount, 2 );
    equal( callback.getCall(0).args[0], 'custom event 1' );
});

test('Also can remove custom events from objects.', function() {
    expect( 5 );

    var spy1 = this.spy();
    var spy2 = this.spy();
    var spy3 = this.spy();

    this.obj.on( 'foo', spy1 );
    this.obj.on( 'bar', spy1 );
    this.obj.on( 'foo', spy2 );
    this.obj.on( 'foo', spy3 );

    // How do you unbind just a single callback for the event?
    this.obj.off( 'foo', spy1 );
    this.obj.trigger( 'foo' );

    ok( spy2.called );

    // How do you unbind all callbacks tied to the event with a single method
    this.obj.off( 'foo' );
    this.obj.trigger( 'foo' );

    ok( spy2.callCount, 1 );
    ok( spy2.calledOnce, "Spy 2 called once" );
    ok( spy3.calledOnce, "Spy 3 called once" );

    // How do you unbind all callbacks and events tied to the object with a single method?
    this.obj.off( 'bar' );
    this.obj.trigger( 'bar' );

    equal( spy1.callCount, 0 );
});
```

###App

��дӦ����������Ĳ���specsҲ�ǳ��б�Ҫ�������ģ�飬setup�������������һ��TodoApp view��Ȼ�����application�ڵ�view�Ƿ���ȷ�Ķ��壬view�Ľ����Ƿ񴥷�collections����ȷ�仯��

```javascript
module( 'About Backbone Applications' , {
    setup: function() {
        Backbone.localStorageDB = new Store('testTodos');
        $('#qunit-fixture').append('<div id="app"></div>');
        this.App = new TodoApp({ appendTo: $('#app') });
    },

    teardown: function() {
        this.App.todos.reset();
        $('#app').remove();
    }
});

test('Should bootstrap the application by initializing the Collection.', function() {
    expect( 2 );

    notEqual( this.App.todos, undefined );
    equal( this.App.todos.length, 0 );
});

test( 'Should bind Collection events to View creation.' , function() {
      $('#new-todo').val( 'Foo' );
      $('#new-todo').trigger(new $.Event( 'keypress', { keyCode: 13 } ));

      equal( this.App.todos.length, 1 );
 });
```

##�����Ķ�����Դ

ʹ��QUnit��SinonJS������Ӧ����һ�ھ���ô���ˡ������㳢����[QUnit Backbone.js Koans](https://github.com/addyosmani/backbone-koans-qunit) ���Ƿ�����չ�����һЩ���ӡ�
�ɲο������������Ķ����ϣ�

* **[Test-driven JavaScript Development (book)](http://tddjs.com/)**
* **[SinonJS/QUnit Adapter](http://sinonjs.org/qunit/)**
* **[SinonJS and QUnit](http://cjohansen.no/en/javascript/using_sinon_js_with_qunit)**
* **[Automating JavaScript Testing With QUnit](http://msdn.microsoft.com/en-us/scriptjunkie/gg749824)**
* **[Ben Alman's Unit Testing With QUnit](http://benalman.com/talks/unit-testing-qunit.html)**
* **[Another QUnit/Backbone.js demo project](https://github.com/jc00ke/qunit-backbone)**
* **[SinonJS helpers for Backbone](http://devblog.supportbee.com/2012/02/10/helpers-for-testing-backbone-js-apps-using-jasmine-and-sinon-js/)**
