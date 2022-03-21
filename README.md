# RockMigrations1

## A message to Russian 🇷🇺 people

If you currently live in Russia, please read [this message](https://github.com/Roave/SecurityAdvisories/blob/latest/ToRussianPeople.md).

[![SWUbanner](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/banner2-direct.svg)](https://github.com/vshymanskyy/StandWithUkraine/blob/main/docs/README.md)

---

This module can be used in parallel to RockMigrations (v2022) for backwards compatibility (in case you need some functionality that the 2022 version of RockMigrations does not provide).

If you are using both modules, the `$rockmigrations` API variable will be the newer version of RM and you can access the old version via `$wire->rockmigrations1`.

## Setup of RM1 + RM

If you are using RockMigrations < 0.0.87 and you want to add the new version of RM to your project do the following:

* Remove RockMigrations from your system by deleting `/site/modules/RockMigrations`
* Clone the new version to `/site/modules/RockMigrations`
* Clone RM1 to `/site/modules/RockMigrations1`
* Do a modules refresh

---

## Field migrations

### Examples

CKEditor field

```php
$rm->migrate([
  'fields' => [
    'yourckefield' => [
      'type' => 'textarea',
      'label' => __('foo bar'),
      'tags' => 'YourModule',
      'inputfieldClass' => 'InputfieldCKEditor',
      'contentType' => FieldtypeTextarea::contentTypeHTML,
    ],
  ],
]);
```

Image field

```php
$rm->migrate([
  'fields' => [
    'yourimagefield' => [
      'type' => 'image',
      'tags' => 'YourTags',
      'maxFiles' => 0,
      'descriptionRows' => 1,
      'extensions' => "jpg jpeg gif png svg",
      'okExtensions' => ['svg'],
      'icon' => 'picture-o',
      'outputFormat' => FieldtypeFile::outputFormatSingle,
      'maxSize' => 3, // max 3 megapixels
    ],
  ],
]);
```

Files field

```php
$rm->migrate([
  'fields' => [
    'yourfilefield' => [
      'type' => 'file',
      'tags' => 'YourTags',
      'maxFiles' => 1,
      'descriptionRows' => 0,
      'extensions' => "pdf",
      'icon' => 'file-o',
      'outputFormat' => FieldtypeFile::outputFormatSingle,
    ],
  ],
]);
```

Options field

```php
$rm->migrate([
  'fields' => [
    'yourfield' => [
      'type' => 'options',
      'tags' => 'YourTags',
      'label' => 'Options example',
      'options' => [
        1 => 'ONE|This is option one',
        2 => 'TWO',
        3 => 'THREE',
      ],
    ],
  ],
]);
```

Page Reference field

```php
$rm->migrate([
  'fields' => [
    'yourfield' => [
      'type' => 'page',
      'label' => __('Select a page'),
      'tags' => 'YourModule',
      'derefAsPage' => FieldtypePage::derefAsPageArray,
      'inputfield' => 'InputfieldSelect',
      'findPagesSelector' => 'foo=bar',
      'labelFieldName' => 'title',
    ],
  ],
]);
```

Date field

```php
$rm->migrate([
  'fields' => [
    'yourfield' => [
      'type' => 'datetime',
      'label' => __('Enter date'),
      'tags' => 'YourModule',
      'dateInputFormat' => 'j.n.y',
      'datepicker' => InputfieldDatetime::datepickerFocus,
      'defaultToday' => 1,
    ],
  ],
]);
```
