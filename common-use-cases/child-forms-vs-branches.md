# Child Forms vs Branches

In Epicollect5 there are two ways to implement nested forms: child forms ([**linking forms using a hierarchy structure**](https://docs.epicollect.net/formbuilder/multiple-forms)) or [**branches**](https://docs.epicollect.net/formbuilder/branches).

While these two approaches look similar, there are some important differences.

{% hint style="success" %}
Nothing stops you from using a combination of hierarchy (child) forms and branches on your project!
{% endhint %}

### Uniqueness

When using a hierarchy structure you can choose between a [**form or a hierarchy uniqueness**](https://docs.epicollect.net/formbuilder/uniqueness). This is not possible when using branches. The branch uniqueness will be limited only to each branch scope as the hierarchy uniqueness cannot be applied.

### Nested forms

When using child forms, you can have only one child form per parent ([**see linking forms**](https://docs.epicollect.net/formbuilder/multiple-forms)). Using branches, you can have multiple branches for a single form. Using branches though, you can go down only one level (it is not possible to add a branch within another branch), while child forms can have a hierarchy of maximum 5 forms.

### Rendering on the mobile app

Child forms and branches are rendered differently on the mobile app.

[**See how to add a child entry**.](https://docs.epicollect.net/web-application/adding-data#add-or-edit-entries-for-multiple-forms-projects)

### Bookmarks

The mobile app [**bookmarks**](https://docs.epicollect.net/mobile-application/add-bookmarks) feature only works with child forms.

### Downloading entries to the mobile app

Branch entries **are not** downloaded to the mobile app, only hierarchy entries are. [**Learn more.**](https://docs.epicollect.net/mobile-application/download-entries)
