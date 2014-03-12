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
   <li>Also translates JavaScripts</li>
   <li>Supports JSON & JSONP</li>
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

<h2>Examples :</h2>

For all examples please open a language directory and write the directory name inside langquery.php relative to the file

For example : 
	langquery.php
	language/en.ini
	language/de.ini
	language/tr.ini
	
<h3>Example 1</h3>
<pre>
<?php
    // Normal usage of the class
    // You can change the language by sending 2 letter language name in any page.
    // Language will be saved into a cookie named 'Language' 
    // Include LangQuery class
    include("LangQuery.php");
    // Everything happens automatically
    $L=new LangQuery();
    
?>
<html>
    <head>
		<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    </head>
    <body>
		<!-- Using Auto Echo feature by adding ">" to the beginning of the key	-->
		<h1><?php $L(">hello") ?></h1>
		<!-- Using regular echo method	-->
		<h2><?php echo($L("hello")) ?></h2>
		<!-- Using instant language change feature. This will change language only for this line. -->
		<p><?php echo($L(">[tr]hello")) ?></p>
		<!-- Using with variables -->
		<p><?php $L(">my_text",25,"Jack Bauer") ?></p>
		<p>
		    Change Language
		    <ul>
			<li><a href="example1.php?Language=tr">Türkçe</a></li>
			<li><a href="example1.php?Language=en">English</a></li>
			<li><a href="example1.php?Language=de">Deutsch</a></li>
		    </ul>
		</p>
    </body>
</html>
</pre>


<h3>Example 2</h3>
<pre>
<?php
    // Using Language class inside strings.
    // Include LangQuery class
    include("LangQuery.php");
    // Everything happens automatically
    $L=new LangQuery();
    
    echo("
	<html>
	    <head>
			<meta http-equiv='Content-Type' content='text/html; charset=UTF-8'>
	    </head>
	    <body>
			<h1>{$L('hello')}</h1>
			<p>{$L('my_text',25,'Jack Bauer')}</p>
			<p>
			    Change Language
			    <ul>
					<li><a href='example2.php?Language=tr'>Türkçe</a></li>
					<li><a href='example2.php?Language=en'>English</a></li>
					<li><a href='example2.php?Language=de'>Deutsch</a></li>
			    </ul>
			</p>
	    </body>
	</html>
    ")
?>
</pre>


<h3>Example 3</h3>
<pre>
<?php
    // In this example author should manage the saving prosedures.
    // Language will not be remembered by cookies.
    // Include LangQuery class
    include("LangQuery.php");
    // Automatic mode closed
    $L=new LangQuery(FALSE);
    
    // Check if $_GET[Language] is valid. 
    // It means there is ini file in language folder
    if($L->is_valid($_GET[Language])){
		// Load Language
		$L->load($_GET[Language]);
    }else{
		$default_language="en";
		// Load $default_language but do not save to cookie.
		$L->load($default_language,FALSE);
    }
?>
<html>
    <head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    </head>
    <body>
	<!-- Using Auto Echo feature by adding ">" to the beginning of the key	-->
	<h1><?php $L(">hello") ?></h1>
	<!-- Using regular echo method	-->
	<h2><?php echo($L("hello")) ?></h2>
	<!-- Using class with variables -->
	<p><?php $L(">my_text",25,"Jack Bauer") ?></p>
	<p>
	    Change Language
	    <ul>
			<li><a href="example3.php?Language=tr">Türkçe</a></li>
			<li><a href="example3.php?Language=en">English</a></li>
			<li><a href="example3.php?Language=de">Deutsch</a></li>
	    </ul>
	</p>
    </body>
</html>
</pre>

<h3>Example 4</h3>
<pre>
<?php
    // Using Javascript
    // You can change the language by sending 2 letter language name in any page.
    // Language will be saved into a cookie named 'Language' 
    // Include LangQuery class
    include("LangQuery.php");
    // Everything happens automatically
    $L=new LangQuery();
    
?>
<html>
    <head>
	    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
	    <!-- Load the same language with the website -->
	    <script src="langquery.php?js"></script>
		<!-- If you want to use a specific language
		<script src="langquery.php?js&Language=de"></script>
		-->
    </head>
    <body>
		<!-- Use in JS just like in php, with the same method name.	-->
		<h1 onclick="alert($L('hello'))"><?php $L(">hello") ?></h1>
		<p onClick="alert($L('my_text',25,'Jack Bauer'))"><?php $L(">my_text",25,"Jack Bauer") ?></p>
		<p>
		    Change Language
		    <ul>
				<li><a href="example1.php?Language=tr">Türkçe</a></li>
				<li><a href="example1.php?Language=en">English</a></li>
				<li><a href="example1.php?Language=de">Deutsch</a></li>
		    </ul>
		</p>
    </body>
</html>
</pre>

