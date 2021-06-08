# til

```php

 $maxItemPerPage =  $request->query->getInt('maxItemPerPage', 12);

 $query = $productRepository->createQueryBuilder('p')
     ->addSelect('pv')  // Save my day :)
     ->join('p.productVariants', 'pv')
     ->where('pv.countryCode = :countryCode')
     ->setParameter('countryCode', 'in')
     //->orderBy('pv.price', 'desc')
     ->getQuery();


 $pagination = $paginator->paginate(
     $query,
     $request->query->getInt('page', 1),
     $maxItemPerPage,
     array('wrap-queries'=>true)
 );

 $pagination->setParam('_locale', $request->get('_locale'));
 $pagination->setParam('_language', $request->get('_language'));


 return $this->render('product/shop.html.twig', [
     'pagination' => $pagination,
     'maxItemPerPage' =>  $maxItemPerPage
 ]);
```

```php
<?php
/** @Entity **/
class User
{
    // ...

    /**
     * @ManyToMany(targetEntity="Group")
     * @OrderBy({"name" = "ASC"})
     **/
    private $groups;
}
```
