# LARAVEL-hiarch

Hierarchical Management for Laravel Projects &amp; Apps. Hiarch Organizes Your Tables, Lists, Menus, Products in Child/Parent With unlimited Levels.   

Hierarchical Management for Laravel Projects & Apps. 

Organizes Your Tables, Lists, Menus and Products in Child/Parent With unlimited Levels. 

What is this?

	Professional Apps present data in organize way, We often call it Child/Parent Management.
	What to do if you have 4 to 15 tables and your app demands or looks great if you have to organize all those tables like Products, Accounts, Customers, Vendors in Child/Parent or Categories / Subcategories methods, I am sure,  lot of hard work/code work  will be involved for each elements to render in HTML sections where its required, and handing of massive code will be another issue.

	Thus at this point, I made this Gadget to solve those issues. This product works with Larval Framework only.

How it Work- Implementation :

	1.	Download Master and Unzip : Get  “yazinc” folder to your laravel “App” Directory. 
	2.	Define your own controller.  Check controller code as below:


            namespace App\Http\Controllers;
            use App\User;
            use App\Http\Controllers\Controller;
            use App\yazinc\hiarch;   	

The last line into Your Controller / Model / Views code will make your Laravel App a “Hiarch” enabled app.

REQUIREMENTS: 

	Any Table in database with record id (int), parent id(int) and Title(chr) fields is qualified for this Gadget. 
	Note: YOU ARE FREE TO NAME DATA FIELD OF YOUR OWN CHOICE,  “parent _id” can be “p_id”, “Tile” can be “description” we will adjust these matters in “Parameters” ahead. 

Calling “hiarch” (Anywhere into Laravel App) :
		Calling “Hairch” From controller to View: 
		class profile extends Controller
		{
						public function index(){
		//*Parameters  array, please change values with your, Table name, your primary key field name, parent id field name, URL where to take after you click, and name your “description or title” field.

		$prams = [
					'table_name'=>"accounts",	
					'id'=>"account_id",	
					'p_id'=>"parent_id",	
					'url'=>"/profile/",
					'title'=>"title",
					];

		hiarch::$prams = $para;
		return view('profile.list', ['data' => hiarch::maping()]);
		}

Calling “Hairch” Direct into View/but with another table data, Call as many as table you can with same method.: 

		<?php 
		use App\yazinc\hiarch;   
		?>
		@extends('layouts.app')
		@section('title', 'by Yasir')
		@section('sidebar')
						@parent
		@endsection
		@section('content')
					<?php 
		$para = 
					[
					'table_name'=>"product",	
					'id'=>"id",	
					'p_id'=>"child",	
					'url'=>"/product/",
					'title'=>"desc",
					];
				hiarch::$prams = $para;
								echo hiarch::maping();
					?>
		@endsection

