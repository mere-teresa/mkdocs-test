#  Converting request parameters into API objects

# Description

In lots of cases, a request will provide a contentId or a locationId. Before using them, you will have to load API object within your controller.

# Solution

For example:

```
public function listBlogPostsAction( $locationId )
{
    $location = $repository->getLocationService()->loadLocation( $locationId );
```

Thanks to the param converter, you can directly have the API object at your disposal. All you have to do is:

-   For Locations:
    -   In your controller's signature, type int the variable to Location.
    -   Make sure a parameter named "locationId" is provided by the request.
-   For Content items:
    -   In your controller's signature, typeint the variable to Content
    -   Make sure a parameter named "contentId" is provided by the request

# Example

Example using Locations:

```
use eZ\Publish\API\Repository\Values\Content\Location;

public function listBlogPostsAction( Location $location )
{
    // use my $location object
```

## Further information

If you want to understand how it works, you can check [Symfony's param converter documentation](http://symfony.com/doc/master/bundles/SensioFrameworkExtraBundle/annotations/converters.html) and the [pull request implementing the Repository ParamConverters](https://github.com/ezsystems/ezpublish-kernel/pull/1128).

## Migrating your current application

[See example pull request on the DemoBundle](https://github.com/ezsystems/DemoBundle/pull/129/files) which provides a few concrete examples.
