langquery
=========

 LangQuery - PHP Multiple Language Class with Parameters

I've looked everywhere for language classes before writing this class but I realized there is no class doing everything i need as easy as in my head.
So I started to write easiest and the best possible language class and I think this class will be number one language class.

<h3>Features :</h3>
<ul>
   <li>Super Easy</li>
   <li>Super Fast</li>
   <li>One line code Setup</li>
   <li>Auto Remember Language</li>
   <li>Auto Detect Browser Language</li>
   <li>Parameter Support</li>
   <li>.ini Based Language Files</li>
   <li>Integrated Change Language Feature</li> 
   <li>Returns String or In-line Echo Feature</li>
</ul>

<h3>Example Code</h3>
<pre>

    include("LangQuery.php");

    $L=new LangQuery();
    // All Setup is ONLY ONE LINE
    // Browser language detected and loaded if available
    // Language will be autosaved and remembered next time.

    // Write Hello World
    echo($L('hello_world'));

    // Write Hello World Easier - In-line Echo Feature
    // You don't have to write echo. Just add '>'
    $L('>hello_world');

    // Use in Strings
    echo("Hello Universe. {$L('hello_world')} Hello Europe");

    // Write my age with parameter
    $L(">my_age",25);

    // Write my name and age with parameters
    $L(">my_name_age","Enes",25);

    // Using instant language change feature.
    // This will change language only for this line. 
    $L(">[tr]hello"));

</pre>
