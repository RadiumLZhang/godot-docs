:github_url: hide

.. DO NOT EDIT THIS FILE!!!
.. Generated automatically from Godot engine sources.
.. Generator: https://github.com/godotengine/godot/tree/master/doc/tools/make_rst.py.
.. XML source: https://github.com/godotengine/godot/tree/master/doc/classes/Expression.xml.

.. _class_Expression:

Expression
==========

**Inherits:** :ref:`RefCounted<class_RefCounted>` **<** :ref:`Object<class_Object>`

A class that stores an expression you can execute.

Description
-----------

An expression can be made of any arithmetic operation, built-in math function call, method call of a passed instance, or built-in type construction call.

An example expression text using the built-in math functions could be ``sqrt(pow(3, 2) + pow(4, 2))``.

In the following example we use a :ref:`LineEdit<class_LineEdit>` node to write our expression and show the result.


.. tabs::

 .. code-tab:: gdscript

    var expression = Expression.new()
    
    func _ready():
        $LineEdit.text_submitted.connect(self._on_text_submitted)
    
    func _on_text_submitted(command):
        var error = expression.parse(command)
        if error != OK:
            print(expression.get_error_text())
            return
        var result = expression.execute()
        if not expression.has_execute_failed():
            $LineEdit.text = str(result)

 .. code-tab:: csharp

    public Expression expression = new Expression();
    
    public override void _Ready()
    {
        GetNode("LineEdit").TextSubmitted += OnTextEntered;
    }
    
    private void OnTextEntered(string command)
    {
        Error error = expression.Parse(command);
        if (error != Error.Ok)
        {
            GD.Print(expression.GetErrorText());
            return;
        }
        object result = expression.Execute();
        if (!expression.HasExecuteFailed())
        {
            GetNode<LineEdit>("LineEdit").Text = result.ToString();
        }
    }



Methods
-------

+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Variant<class_Variant>`         | :ref:`execute<class_Expression_method_execute>` **(** :ref:`Array<class_Array>` inputs=[], :ref:`Object<class_Object>` base_instance=null, :ref:`bool<class_bool>` show_error=true, :ref:`bool<class_bool>` const_calls_only=false **)** |
+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`String<class_String>`           | :ref:`get_error_text<class_Expression_method_get_error_text>` **(** **)** |const|                                                                                                                                                        |
+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`bool<class_bool>`               | :ref:`has_execute_failed<class_Expression_method_has_execute_failed>` **(** **)** |const|                                                                                                                                                |
+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Error<enum_@GlobalScope_Error>` | :ref:`parse<class_Expression_method_parse>` **(** :ref:`String<class_String>` expression, :ref:`PackedStringArray<class_PackedStringArray>` input_names=PackedStringArray() **)**                                                        |
+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Method Descriptions
-------------------

.. _class_Expression_method_execute:

- :ref:`Variant<class_Variant>` **execute** **(** :ref:`Array<class_Array>` inputs=[], :ref:`Object<class_Object>` base_instance=null, :ref:`bool<class_bool>` show_error=true, :ref:`bool<class_bool>` const_calls_only=false **)**

Executes the expression that was previously parsed by :ref:`parse<class_Expression_method_parse>` and returns the result. Before you use the returned object, you should check if the method failed by calling :ref:`has_execute_failed<class_Expression_method_has_execute_failed>`.

If you defined input variables in :ref:`parse<class_Expression_method_parse>`, you can specify their values in the inputs array, in the same order.

----

.. _class_Expression_method_get_error_text:

- :ref:`String<class_String>` **get_error_text** **(** **)** |const|

Returns the error text if :ref:`parse<class_Expression_method_parse>` has failed.

----

.. _class_Expression_method_has_execute_failed:

- :ref:`bool<class_bool>` **has_execute_failed** **(** **)** |const|

Returns ``true`` if :ref:`execute<class_Expression_method_execute>` has failed.

----

.. _class_Expression_method_parse:

- :ref:`Error<enum_@GlobalScope_Error>` **parse** **(** :ref:`String<class_String>` expression, :ref:`PackedStringArray<class_PackedStringArray>` input_names=PackedStringArray() **)**

Parses the expression and returns an :ref:`Error<enum_@GlobalScope_Error>` code.

You can optionally specify names of variables that may appear in the expression with ``input_names``, so that you can bind them when it gets executed.

.. |virtual| replace:: :abbr:`virtual (This method should typically be overridden by the user to have any effect.)`
.. |const| replace:: :abbr:`const (This method has no side effects. It doesn't modify any of the instance's member variables.)`
.. |vararg| replace:: :abbr:`vararg (This method accepts any number of arguments after the ones described here.)`
.. |constructor| replace:: :abbr:`constructor (This method is used to construct a type.)`
.. |static| replace:: :abbr:`static (This method doesn't need an instance to be called, so it can be called directly using the class name.)`
.. |operator| replace:: :abbr:`operator (This method describes a valid operator to use with this type as left-hand operand.)`
