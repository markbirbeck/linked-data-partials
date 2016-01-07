# linked-data-partials

Linked Data partials for inclusion in templates, implementing classes from [Schema.org](http://schema.org/).

## Motivation

To come up with a set of partials that:

* are useful in such a large number of situations that lots of people will went to help keep them up-to-date, for everyone's benefit;
* are provided as a module so that they can be easily imported into apps such as static-site generators (SSGs), web servers, mail servers, and so on. Being a module means that we also benefit from versioning;
* use as much semantic HTML as possible, and continue to evolve with 'best practice';
* contain no styling so as not to restrict their use (this is not just avoiding the use of `@style`, but also excluding uses of `@class` that are only for appearance);
* include `@property` and `@typeof` attributes with values that align with Schema.org;
* use template variables that also match the Schema.org properties so as to reduce the need to look up the names for values in different parts of a system.

This final point simply means that software making use of these partials, such as SSGs, should use variables named the same as those used in Schema.org, when providing the values to be injected. For example, the title of a blog post using the `BlogPosting` class would be `headline` rather than `title`.

## Example

To illustrate the kind of markup that is being used in the partials, here's a segment of the partial for the Schema.org `BlogPosting` class. This class includes properties such as `articleBody` and `headline`, and these are included in the `BlogPosting` partial as follows:

```html
<article vocab="http://schema.org/" typeof="BlogPosting">
  <header>
    <h3 property="headline">{{ headline }}</h3>
  </header>
  <div property="articleBody">
    {{ articleBody }}
  </div>
</article>
```

The key points to note are:

* that the RDFa `@property` values for Schema.org are provided, and;
* the template variables have *exactly* the same name as the values in the `BlogPosting` class.

## Currently Implemented Partials

The following partials have been added:

### Blog

A blog, which is a collection of blog posts.

### BlogPosting

An individual blog post.

### Organization

An organisation.

### SportsEvent

A sports event.

## To Do

There is still work to do in the `Blog` partial to align the object properties with the names of the properties in Schema.org, since at the moment these are determined by static-site generators. This will be addressed, though.

There's also a bit of markup that needs to be removed, but changes in some other modules need to happen first.

There are lots of partials that it would be useful to add.

## Getting Involved

More partials are of course welcome, but it's just as important to ensure that partials use the best possible markup, and provide as many properties from the Schema.org classes as possible. Any discussion on these aspects of partials will therefore be most welcome.
