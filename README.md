ngEkathuwa
==========

#### Angularjs Bootstrap 3 Modal service - Ekathuwa
==============================================
[Examples: ngEkathuwa](http://plnkr.co/ebDtSMw6w0IZquaglEMe)

###### This given you to easily handle Bootstrap 3 Modal window with Angularjs.
###### It is more flexible...
###### It is responsive...
###### Can be use custom sizes...
###### Working with templates...
###### It used promisses when you need...

#### Getting Start

1. Include `<link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.0.0/css/bootstrap.min.css">` in the head of your document.
2. Include `<script src="//ajax.googleapis.com/ajax/libs/angularjs/1.2.0rc1/angular.min.js"></script>`
3. Include ` <script src="//netdna.bootstrapcdn.com/bootstrap/3.0.0/js/bootstrap.min.js"></script>`
4. Then include `ekathuwa.min.js`
5. Declare a module dependency, in your module `'[ngEkathuwa']`
6. Declare a controller dependency, in your controller `$ekathuwa`
7. Then use it `$ekathuwa.modal(options)`



#### Ekathuwa API and exampls
=============================

##### ngEkathuwa Options
<pre>
Default options
-------------------------
id:                (string)    "ekathuwaModalID"
scope:                         $rootScope
controller:        (string)    null
show:              (boolean)   true
backdrop:          (boolean)   true
keyboard:          (boolean)   true
remote:            (boolean)   false
contentStyle:      (string)    null
contentCustomSize: (number)    0
contentPreSize:    (string)    "df", //df,sm,md,lg,fl
templateURL:       (string)    null
templateHTML:      (string)    null
bodyTemplateURL:   (string)    null
bodyTemplate:      (string)    null
header:            (boolean)   true
headerText:        (string)    null
headerTemplate:    (string)    null
headerCloseBtn:    (boolean)   true
footer:            (boolean)   true
footerTemplate:    (string)    null
footerCloseBtn:    (boolean)   true
footerSaveBtn:     (boolean)   false
</pre>

    //Basic Modal
    $scope.ekathuwaModalBasic = function () {
        $ekathuwa.modal({
            id: "ekathuwaModalBasicId",
            headerText:"Ekathuwa modal header",
        });
    }

    //Fullscreen Modal
    $scope.ekathuwaModalTemp = function () {
        $ekathuwa.modal({
            id: "ekathuwaModalTempId",
            scope: $scope,
            templateURL: "modal-template.html",
            contentPreSize: "fl"
        });
    }

    //Modal by template with stylish(350px width overwrite from 80%)
    $scope.ekathuwaModalStyle = function () {
        $ekathuwa.modal({
            id: "ekathuwaModalTempId",
            scope: $scope,
            templateURL: "modal-template.html",
            contentStyle: "width:350px;heigth:400px;background-color:#1b78f7;",
            contentCustomSize: 80
        });
    }

    //Large screen modal with inline html
    $scope.ekathuwaModalTempHTML = function () {
        $ekathuwa.modal({
            id: "ekathuwaTemlHTMLId",
            scope: $scope,
            contentPreSize: "lg",
            templateHTML: '<div aria-hidden="true" aria-labelledby="myModalLabel" role="dialog" tabindex="-1" class="modal fade" id="ekathuwaTemlHTMLId" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-header"><button aria-hidden="true" data-dismiss="modal" class="close" type="button">x</button><h4 id="myModalLabel" class="modal-title">Ekathuwa Modal Heading</h4></div><div class="modal-body"><h4>Ekathuwa modal body.</h4><button class="btn btn-warning" ng-click="btnMsgFromCntl()">Get Message</button><div class="modal-footer"><button data-dismiss="modal" class="btn btn-default" type="button">Close</button><button class="btn btn-primary" type="button">Save changes</button></div></div></div></div>'
        });
    }

    //Modal body from template and set header text
    $scope.ekathuwaModalBodyTempURL = function () {
        $ekathuwa.modal({
            id: "ekathuwaBodyTempLId",
            scope: $scope,
            headerText:"Ekathuwa modal header",
            bodyTemplateURL: 'modal-template-body.html'
        });
    }

    //Footerless modal
    $scope.ekathuwaModalFooterless = function () {
        $ekathuwa.modal({
            id: "ekathuwaBodyTempLId",
            scope: $scope,
            headerText:"Ekathuwa modal header",
            bodyTemplateURL: 'modal-template-body.html',
            footer:false
        });
    }

    //Headerless modal
    $scope.ekathuwaModalHeaderless = function () {
        $ekathuwa.modal({
            id: "ekathuwaBodyTempLId",
            scope: $scope,
            bodyTemplateURL: 'modal-template-body.html',
            header:false
        });
    }

    //Modal in promisses
    var ekathuwaModalPromise = $ekathuwa.modal({
        id: "ekathuwaBodyPromiseId",
        scope: $scope,
        show: false,
        bodyTemplateURL: 'modal-template-body.html'
    });
    $q.when(ekathuwaModalPromise).then(function (m) {
        m.modal('show'); //for  hide => m.modal('hide');
    });

<table>
    <tr>
        <th width="10%">Option</th>
        <th width="10%">Value</th>
        <th width="80%">Description</th>
    </tr>
    <tr>
        <td>
            <code>id</code>
        </td>
        <td>
            <code>default: ekathuwaModalID</code>
        </td>
        <td>Set your modal ID.
            <br/>Id avoid namespace collisions.Most important, when modal inside modal(nested modal)</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({id:"yourModalId"});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>scope</code>
        </td>
        <td>
            <code>default: $rootScope</code>
        </td>
        <td>Pass your scope.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({scope:$scope});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>controller</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Pass your controller.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({controller:"ekathuwaModalCtl"});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>show</code>
        </td>
        <td>
            <code>default: true</code>
        </td>
        <td>Shows the modal when initialized.
            <br/>You can show/hide modal using promisses.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>var p = $ekathuwa.modal({id:"modalPromisses",show:false});</pre>
            <pre>$q.when(p).then(function (m) { m.modal('show'); });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>backdrop</code>
        </td>
        <td>
            <code>default: true</code>
        </td>
        <td>Includes a modal-backdrop element. Alternatively, specify
            <code>static</code>for a backdrop which doesn't close the modal on click.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({backdrop:"static"});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>keyboard</code>
        </td>
        <td>
            <code>default: true</code>
        </td>
        <td>Closes the modal when escape key is pressed</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({keyboard:false});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>contentStyle</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Set modal style.If you set
            <code>width</code>, modal not be responsive. Use "
            <code>;</code>" for style seperation.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({id:"yourModalId",contentStyle:"width:350px;heigth:400px;background-color:red;"});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>contentCustomSize</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Set modal percentage(%) width. Not need to mention "%", Only need value.
            <br/>It overwrite contentStyle's width.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({id:"yourModalId",contentStyle:"width:350px;heigth:400px;background-color:#1b78f7;",contentCustomSize:80});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>contentPreSize</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Set modal width by inbuild value.
            <br/>
            <code>df= Bootstrap's default modal width</code>
            <br/>
            <code>sm= small width</code>
            <br/>
            <code>md= medium width</code>
            <br/>
            <code>lg= large width</code>
            <br/>
            <code>fl= full width</code>
        </td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({id:"yourModalId",contentStyle:"width:350px;heigth:400px;background-color:#1b78f7;",contentPreSize:'lg'});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>templateURL</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Pass your HTML modal page template as URL.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalTempId", scope: $scope, templateURL: "./views/modal-template1.html" });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>templateHTML</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Pass your modal page as HTML tags. This required nessery HTML elements for show modal. Refer Bootstrap3 document.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: 'ekathuwaTemlHTMLId', scope: $scope, contentPreSize: 'fl', templateHTML:''});</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>bodyTemplateURL</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Pass your modal page's body as template URL.
            <br/>It used default header and footer.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaBodyTempLId", scope: $scope, bodyTemplateURL: './views/modal-template-body.html' });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>bodyTemplate</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Pass your modal page's body as inline HTML.
            <br/>It used default header and footer. Discard when you set
            <code>bodyTemplateURL</code>
        </td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaBodyTempLHTMLId", scope: $scope, bodyTemplate: 'This is a modal body' });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>header</code>
        </td>
        <td>
            <code>default: true</code>
        </td>
        <td>Set modal header visible or not.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalId", scope: $scope, header: false });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>headerTemplate</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Pass your modal header as inline HTML.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalId", scope: $scope, headerTemplate: 'This is a modal header' });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>headerText</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Set header text.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalId", scope: $scope, headerText: "This is header" });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>headerCloseBtn</code>
        </td>
        <td>
            <code>default: true</code>
        </td>
        <td>Show/Hide header close button.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalId", scope: $scope, headerCloseBtn: false });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>footer</code>
        </td>
        <td>
            <code>default: true</code>
        </td>
        <td>Set modal footer visible or not.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalId", scope: $scope, footer: false });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>footerTemplate</code>
        </td>
        <td>
            <code>default: null</code>
        </td>
        <td>Pass your modal footer as inline HTML.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalId", scope: $scope, footerTemplate: 'This is footer' });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>footerCloseBtn</code>
        </td>
        <td>
            <code>default: true</code>
        </td>
        <td>Show/Hide footer close button.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalId", scope: $scope, footerCloseBtn: false });</pre>
        </td>
    </tr>
    <tr>
        <td>
            <code>footerSaveBtn</code>
        </td>
        <td>
            <code>default: false</code>
        </td>
        <td>Show/Hide footer save button.</td>
    </tr>
    <tr>
        <td colspan="3">
            <pre>$ekathuwa.modal({ id: "ekathuwaModalId", scope: $scope, footerSaveBtn: true });</pre>
        </td>
    </tr>
</table>

### License

Copyright 2013 Sarath Ambegoda. Released under the [MIT License (MIT)](LICENSE).
