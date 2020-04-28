---
title: Advanced Programming with Python. Session 7
author: Pepe García
email: jgarciah@faculty.ie.edu
date: 2020-04-20
lang: en
---

Advanced Programming with Python. Session 7
===========================================


Dash
====

https://dash.plot.ly

 

Dash is a library for creating data visualizations

Dash. Layout
============

We can create HTML layouts directly in Python with Dash

    import dash_core_components as dcc
    import dash_html_components as html

    html.Div(children = [
        html.H1("title"),
        dcc.Dropdown(
            id="district",
            options=districts,
            multi=True,
            value=[districts[0]["value"]]
        )
    ])

Dash. Graphs
============

    import dash_core_components as dcc
    import dash_html_components as html

    dcc.Graph(
        id='first-graph',
        figure={
            'data': [
                {'x': [1, 2, 3], 'y': [4, 1, 2], 'type': 'bar', 'name': 'bar1'},
                {'x': [1, 2, 3], 'y': [2, 4, 5], 'type': 'bar', 'name': 'bar2'},
            ],
            'layout': {
                'title': 'Dash Data Visualization'
            }
        }
    )

Practice
========

see **session-7/example-1**

Dash. Callbacks
===============

**callbacks** make our Dash applications interactive.  They\'re
functions that whenever an **input** component changes, will change an
**output** component

    @app.callback(
        Output(component_id="accidents-graph",component_property="figure"),
        [Input(component_id="district", component_property="value")]
    )
    def update(districts):
        pass

Practice
========

let\'s see

**example-2-callbacks/simple\_callback.py**

Practice
========

But, callbacks can do much more than that, they can modify graphs
whenever some component value is changed by the user \
\
let\'s see

**example-3-callbacks/more\_callbacks.py**

Dash. More interesting example
==============================

All the examples we\'ve seen so far fairly simple, let\'s see a more
interesting example in

 

**example-3/server.py**

Exercise
========

Modify example-3 so that it filters by

accident type (**TIPO ACCIDENTE**) too
