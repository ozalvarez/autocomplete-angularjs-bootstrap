# autocomplete-angularjs-bootstrap
Here some snippet of how to create an autocomplete using angular.js and bootstrap. You don't need to add external libraries

## The View
```
<input type="text" class="form-control" ng-change="loadCategories(queryCategories)" ng-model="queryCategories" />
<div class="list-group list-group-autocomplete" ng-show="categories!=null && categories.length>0">
    <a ng-click="addCategory(item)" href="" class="list-group-item" ng-repeat="item in categories">
        {{item.CategoryAlias}}
    </a>
</div>
<button class="btn btn-sm btn-default" ng-repeat="item in model.ProductCategories" ng-show="model.ProductCategories.length>0" ng-click="removeCategory(item)">
    {{item.CategoryName}} <i class="fa fa-remove"></i>
</button>
```
## The Controller
 ```
$scope.loadCategories = function (query) {
    productService.getCategories(query).then(function (data) {
        $scope.categories = data;
    });
};
$scope.addCategory = function (item) {
    $scope.model.ProductCategories.push(item);
    $scope.categories = [];
    $scope.queryCategories = "";
};
$scope.removeCategory = function (item) {
    var index=$scope.model.ProductCategories.indexOf(item);
    $scope.model.ProductCategories.splice(index, 1);
};
```
## The CSS
 ```
 .list-group-autocomplete{
    position:fixed; 
    z-index:100;
}
 ```
