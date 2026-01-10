# Next.js Basics

## Introduction#

## Project Structure

- the folders inside the `app` dir define url routes:  path `app/blog/authors/page.tsx` becomes url `/blog/authors'
- but routes are only accessible if a`page.js` or `route.js` file exists
- folders starting with a `_dirName` are private
- folders in brackets `(dirName)` are used for structuring and are ignored in the url
- folders in square brackets `[dirName]` are parameterized by the `params` property

- special files
	- `page.js` defines a page, accessible through the url from the dir path
	- `layout.js` is shared across pages (for example for header bars)
		- it accepts a children property which can be a page or another layout
---

Origin: https://nextjs.org/docs/app/getting-started
References: 
Tags: 
Created: 07.01.2026

