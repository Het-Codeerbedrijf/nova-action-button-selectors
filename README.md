# Laravel Nova action button selector

[![Packagist Version](https://img.shields.io/packagist/v/lemonlabs/nova-action-button-selectors.svg?style=for-the-badge)](https://packagist.org/packages/lemonlabs/nova-action-button-selectors)
[![Packagist Downloads](https://img.shields.io/packagist/dt/lemonlabs/nova-action-button-selectors.svg?style=for-the-badge)](https://packagist.org/packages/lemonlabs/nova-action-button-selectors)

This package allows you to add buttons for Nova actions on the detail page instead having them all within the dropdown menu.

This package is forked from [`lednerb/nova-action-button-selectors`](https://codeberg.org/Lednerb/nova-action-button-selectors)

## Requirements
- `php: ^8`
- `laravel/nova: ^4|^5`

## How to install
```
composer require lemonlabs/nova-action-button-selectors
```
Detail page
![example_1](./docs/main_1.jpg)

Index page with inline action
![example_2](./docs/main_2.jpg)


## Usage

In your Action class define the following trait:

```php
...
use LemonLabs\ActionButtonSelector\ShowAsButton;

class MyAction extends Action
{
    use InteractsWithQueue, Queueable;
    use ShowAsButton;

    ...
```

If you want to hide the button on some Detail pages, use the following method in the Nova Model's `actions` array:

```php
...
 public function actions(NovaRequest $request)
    {
        return [
            MyCustomAction::make()
                ->onlyOnDetail()
                ->withoutConfirmation()
                ->showAsButton(false),

            ...
```
