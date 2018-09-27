<p>What is this?</p>
<p>Professional Apps present data in organize way, We often call it Child/Parent Management.<br>
What to do if you have 4 to 15 tables and your app demands or looks great if you have to organize all those tables like Products, Accounts, Customers, Vendors in Child/Parent or Categories / Subcategories methods, I am sure,  lot of hard work/code work  will be involved for each elements to render in HTML sections where its required, and handling of massive code will be another issue.</p>
<pre><code>Thus at this point, I made this Gadget to solve those issues. This product works with Larval Framework only.
</code></pre>
<p>How it Work- Implementation :</p>
<p>Download Master and Unzip : Get  “yazinc” folder to your laravel “App” Directory.<br>
Define your own controller.  Check controller code as below:</p>
<pre><code>&lt;?php
namespace App\Http\Controllers;
use App\User;
use App\Http\Controllers\Controller;
use App\yazinc\hiarch;      
?&gt;
</code></pre>
<p>The last line into Your Controller / Model / Views code will make your Laravel App a “Hiarch” enabled app.</p>
<p>REQUIREMENTS:</p>
<p>Any Table in database with record id (int), parent id(int) and Title(chr) fields is qualified for this Gadget.<br>
Note: YOU ARE FREE TO NAME DATA FIELD OF YOUR OWN CHOICE,  “parent _id” can be “p_id”, “Tile” can be “description” we will adjust these matters in “Parameters” ahead.</p>
<p>Calling “hiarch” (Anywhere into Laravel App) :<br>
Calling “Hairch” From controller to View:</p>
<pre><code>&lt;?php
class profile extends Controller
{
         public function index(){

//*Parameters  array, please change values with your, 
Table name, your primary key field name, parent id field 
name, URL where to take after 
you click, and name your 
“description or title” field.

$prams = [
        'table_name'=&gt;&quot;accounts&quot;,   
        'id'=&gt;&quot;account_id&quot;, 
        'p_id'=&gt;&quot;parent_id&quot;,    
        'url'=&gt;&quot;/profile/&quot;,
        'title'=&gt;&quot;title&quot;,
        ];
hiarch::$prams = $para;
return view('profile.list', ['data' =&gt; hiarch::maping()]);
}
?&gt;
</code></pre>
<p>Calling “Hairch” Direct into View/but with another table data, Call as many as table you can with same method.:</p>
<pre><code>&lt;?php 
use App\yazinc\hiarch;   
?&gt;
@extends('layouts.app')
@section('title', 'by Yasir')
@section('sidebar')
    @parent
@endsection
@section('content')

   &lt;?php 
$para = 
        [
        'table_name'=&gt;&quot;product&quot;,    
        'id'=&gt;&quot;id&quot;, 
        'p_id'=&gt;&quot;child&quot;,    
        'url'=&gt;&quot;/product/&quot;,
        'title'=&gt;&quot;desc&quot;,
        ];
        hiarch::$prams = $para;
            echo hiarch::maping();
   ?&gt;
@endsection
</code></pre>

for More information on this Topic:
 
https://support.commoncontrolshub.com/hc/en-us/articles/115001917806-Select-a-hierarchical-level-for-the-Asset-

Hierarchical structure of product categories:

https://developer.intuit.com/hub/blog/2015/10/23/item-hierarchies-using-categories-coming-in-quickbooks

