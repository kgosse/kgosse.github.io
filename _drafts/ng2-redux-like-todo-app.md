---
layout: post
title:  "Angular 2 Redux-like Todo App"
categories: javascript angular2 typescript
comments: true
---

* content
{:toc}

## Introduction 

<small>Before everything, I would like to say that english is not my mother tongue. I speak french. So be nice :-)  
Feel free to email me or to leave a comment if you see any kind of mistake. I'll appreciate it. Thanks.</small>

I did the classical todo app in angular 2. You can test the work by clicking on this:
[view app][1]  
The project is on github: [sources][2]

By the time I'm writing this post, angular 2 is still in release candidate version. So my goal was
to play with this new framework by making a somewhat useful project.

## Getting Started

Make sure you have have [NodeJS][3] and [Git][4] installed on your machine. Then do this:

{% highlight sh %}
42sh> # install webpack, webpack-dev-server and typings globally
42sh> npm i -g webpack webpack-dev-server typings
42sh> git clone https://github.com/kgosse/ng2todoapp.git
42sh> cd ng2todoapp
42sh> npm i
42sh> npm start
{% endhighlight %}

If everything is ok, open your browser and go to: [localhost:8080][5]

## Components

Here is how the user interface is structured :  

![Components' structure image][ComponentsStructure]

## The application's logic

A todo is represented by this class :

{% highlight javascript %}
// src/store/index.js

export class Todo {
    done: Boolean;
    editing: Boolean;

    private _text: String;
    get text() {
        return this._text;
    }
    set text(value: String) {
        this._text = value.trim();
    }

    constructor(text: String) {
        this.done = false;
        this.editing = false;
        this.text = text.trim();
    }
}
{% endhighlight %}

Then we have the TodoStore class to manage all the todos:

{% highlight javascript %}
// src/store/index.ts

export class TodoStore {
    todos: Array<Todo>;

    constructor() {
    //...
    }

    private getTasks(done: Boolean) {
    //...
    }
    
    updateStore() {
    //...
    }
    
    removeDoneTasks() {
    //...
    }

    getRemaining() {
    //...
    }

    getDoneTasks() {
    //...
    }

    toggleTask(todo: Todo) {
    //...
    }

    add(todo: Todo) {
    //...
    }

    toggleAll() {
    //...
    }

    remove(todo: Todo) {
    //...
    }
}
{% endhighlight %}

Finally, I have created a service (src/services/todo.services.ts) which is injected in all the components. Notice that this service is the only way
for the components to interact with the TodoStore. The thing I like the most with this service is that it helps synchronising
the application's state between the components. Consider the following case: The user decides to show only the remaining todos
by selecting the appropriate status in the select input. How to make the TodoListComponent refresh its content according to the new
status selected ? My solution was to add an EventEmitter member attribute inside the TodoService. As it is injected in all the components,
they can subscribe to that attribute (todoEvent) in order to listen and handle emitted actions and also use it to emit their own actions. That way,
when the StatusSelector component emit an action (STATUS_CHANGE) for a change inside the select input, here is how this one is handled inside the
TodoList component :

{% highlight javascript %}
    // src/components/todo-list.ts

    constructor(private _todoService: TodoService){
        this._todoService.todoEvent.subscribe((action:Action) => {
            switch (action.type) {
                case ARCHIVE:
                    this.getTodos();
                    break;
                case STATUS_CHANGE:
                    if (action.payload === ALL)
                        this.getTodos();
                    this._status = action.payload;
                    break;
                case TEXT_CHANGE:
                    this._text = action.payload;
                    break;
            }
        });
    }
{% endhighlight %}

## Useful Links

* [official todomvc with angular 2](https://github.com/tastejs/todomvc/tree/master/examples/angular2)
* [official todomvc site](http://todomvc.com/)

## Conclusion

Angular 2 is a very interesting framework. It comes with all the things to let you have a very solid MVC structure
(like angular 1). But, since I have started developing apps using [flux pattern][flux] thanks to [React][react], I fall in love with
it. That's why, even if this app is working properly, I'm going to make another version of it in [flux][flux] and [Redux][redux] way.
Thanks for reading :-)


[1]:https://kgosse.github.io/ng2todoapp
[2]:https://github.com/kgosse/ng2todoapp
[3]:https://nodejs.org/en/
[4]:https://git-scm.com/
[5]:https://locahlhost:8080
[react]:https://facebook.github.io/react/
[redux]:http://redux.js.org/index.html
[flux]:https://facebook.github.io/flux/docs/overview.html
[ComponentsStructure]:{{"/static/images/ComponentsStructure.png" | prepend: site.baseurl }}
