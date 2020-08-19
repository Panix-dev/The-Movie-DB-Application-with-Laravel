# The Movie DB Application using Laravel and Laravel Livewire

> An example of how to implement some of the new features of Laravel 7 like the HTTP Client and Blade Components 

A Movie Application using Laravel, Tailwind CSS and The Movie DB REST API to retrieve all movie data. The application is based on the Laravel Framework making use of several Laravel 7 features like the HTTP Client and Blade Components. The application also makes use of Alpine.js and Laravel Livewire to provide some reactivity and improve the user's experience.


## Table of Contents


> Try `clicking` on each of the `anchor links` below so you can get redirected to the appropriate section.

- [The Movie DB](#the-movie-db)
- [Laravel Livewire](#laravel-livewire)
- [Tailwind CSS](#laravel-livewire)
- [Alpine Js](#alpine-js)
- [HTTP Client](#http-client)
- [Blade Components](#blade-components)
- [Contact Details](#contact-details)
- [Inspiration](#inspiration)


## The Movie DB


<br/>
<img src="https://www.themoviedb.org/assets/2/v4/logos/v2/blue_short-8e7b30f73a4020692ccca9c88bafe5dcb6f8a62a4c6bc55cd9ba82bb2cd95f6c.svg" width="250 title="The Movie DB" alt="The Movie DB">

The Movie Database (TMDb) is a community built movie and TV database. Every piece of data has been added by the amazing community dating back to 2008. TMDb's strong international focus and breadth of data is largely unmatched. Put simply, they live and breathe community and that's precisely what makes them different.

- :link: [The Movie DB (TMDb)](https://www.themoviedb.org/)


## Laravel Livewire


<br/>
<img src="https://pagapiou.com/images/laravel-livewire.png" title="Laravel Livewire" alt="Laravel Livewire">

Livewire is a full-stack framework for Laravel that makes building dynamic interfaces simple, without leaving the comfort of Laravel. 


- :link: [Laravel Livewire](https://laravel-livewire.com/)


```php
public $search = '';
    
public function render()
{
	$searchResults = [];

	if(strlen($this->search) >= 2) {
		$searchResults = Http::withToken(config('services.tmdb.token'))
        ->get('https://api.themoviedb.org/3/search/movie?query='.$this->search)
        ->json()['results'];
	}

    return view('livewire.search-dropdown', [
    	'searchResults'	=>	collect($searchResults)->take(7),
    ]);
}
```


```javascript
<input 
	wire:model.debounce.500ms="search"
	type="text"
	class="bg-gray-800 rounded-full text-sm w-64 px-4 pl-8 py-1 focus:outline-none focus:shadow-outline"
	placeholder="Search"
	x-ref="search"
	@keydown.window="
		if(event.keyCode === 191) {
			event.preventDefault();
			$refs.search.focus();
		}
	"
	@focus="isOpen = true"
	@keydown="isOpen = true"
	@keydown.escape.window="isOpen = false"
	@keydown.shift.tab="isOpen = false"
>

<div wire:loading class="spinner top-0 right-0 mr-4 mt-3"></div>
```


## Tailwind CSS


Tailwind CSS is a highly customizable, low-level CSS framework that gives you all of the building blocks you need to build bespoke designs without any annoying opinionated styles you have to fight to override.

- :link: [Tailwind CSS](https://tailwindcss.com/)


## Alpine Js


Alpine.js offers you the reactive and declarative nature of big frameworks like Vue or React at a much lower cost. You get to keep your DOM, and sprinkle in behavior as you see fit.


- :link: [Alpine.js](https://github.com/alpinejs/alpine)


## HTTP Client


```php
$popularMovies = Http::withToken(config('services.tmdb.token'))
	->get('https://api.themoviedb.org/3/movie/popular')
	->json()['results'];
```


## Blade Components


```php
@foreach($popularMovies as $movie)
	<x-movie-card :movie="$movie" />
@endforeach
```


## Contact Details


> :computer: [https://pagapiou.com](https://pagapiou.com)

> :email: [hello@pagapiou.com](mailto:hello@pagapiou.com)

> :iphone: [LinkedIn](https://www.linkedin.com/in/agapiou/)

> :iphone: [Instagram](https://www.instagram.com/panos_agapiou/)

> :iphone: [Facebook](https://www.facebook.com/panagiotis.agapiou)


## Inspiration


- **[Andre Madarang](https://www.youtube.com/channel/UCtb40EQj2inp8zuaQlLx3iQ)**
