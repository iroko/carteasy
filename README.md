[![Android Arsenal]( https://img.shields.io/badge/Android%20Arsenal-Carteasy-green.svg?style=flat )]( https://android-arsenal.com/details/1/7585 )

# Carteasy

   A Shopping cart library for Android that allows you add to add items to cart and retrieve at ease using JSONObjects.

## Quick Start

  Add the following dependency to your build.gradle:

  Dependencies will come here.

  For Gradle:
 ```
implementation 'com.carteasy.v1.lib:carteasy:0.0.6'
 ```

  For Maven: include maven url to repositories in build.gradle (module)
 ```
allprojects {
    repositories {
        jcenter()
        maven {
            url  "http://dl.bintray.com/tosinmath007/Carteasy"
        }
    }
}
 ```



You should then checkout the library and investigate the sample code, which covers some of the features.

<image of sample app here>

## Usage

 *Adding items to cart*

 ```
 Carteasy cs = new Carteasy();
 cs.add(String id, String key, Object value);
 cs.commit(getApplicationContext());
 ```

 ```
 cs.add("Your Product Id", "key", "value");
 ```


 Your product items is tied to your Id and can be retrieved anytime the Id is produced.

 ```
 String productIdOne = "e400";
 String productIdTwo= "e401";
 ```

 ```
 Carteasy cs = new Carteasy();

 cs.add(productIdOne, "product name", "Marlboro");
 cs.add(productIdOne, "product description", "cigarate box");
 cs.add(productIdOne, "product price", 200.00);
 cs.add(productIdOne, "quantity", 5);
 cs.add(productIdOne, "currency", "dollar");
 ...
 cs.commit(getApplicationContext());

 cs.add(productIdTwo, "product name", "Starbucks coffee");
 cs.add(productIdTwo, "product description", "coffee bags");
 cs.add(productIdTwo, "product price", 100.00);
 cs.add(productIdTwo, "quantity", 9);
 cs.add(productIdTwo, "currency", "dollar");
 ...
 cs.commit(getApplicationContext());
 ```

 *Always keep data even when app is closed*

  ```
cs.persistData(getApplicationContext(), true);
 ```


 *Retrieve item by Id and key*

 Returns an object. you can use it as an object or typecast it to what ever you want

 ```
 Carteasy cs = new Carteasy();
 Object value = cs.get( String id, String key, getApplicationContext());
 ```

 Returns a String

 ```
 Carteasy cs = new Carteasy();
 String value = cs.getString( String id, String key, getApplicationContext());
 ```

 You can return type of value using either of these below:

 *String*

 ```
 String value = cs.getString(String id, String key, Context context);
 ```

 *Integer*

 ```
 int value = cs.getInteger(String id, String key, Context context);
 ```

 *Float*

 ```
 Float value = cs.getFloat(String id, String key, Context context);
 ```

 *Double*

 ```
 Double value = cs.getDouble(String id, String key, Context context);
 ```

 *Long*

 ```
 Long value = cs.getLong(String id, String key, Context context);
 ```

 *Short*

 ```
 Short value = cs.getShort(String id, String key, Context context);
 ```


 *Update Items*

 To update a items value, you have to pass the id, key and your newValue as parameters

 ```
 Carteasy cs = new Carteasy();
 cs.update(String id, String key, Object newValue, Context context);
 ```

 *Removing specific item value from cart*

 ```
 Carteasy cs = new Carteasy();
 cs.Removekey(String id, String key, Context context);
 ```

 *Removing item and its property value from cart*

 ```
 Carteasy cs = new Carteasy();
 cs.RemoveId(String id, Context context);
 ```

  *Clearing all items from cart*

  ```
  Carteasy cs = new Carteasy();
  cs.clearCart(Context context);
  ```


 *Viewing all items stored in cart*

 ```
  Map<Integer, Map> data;
  Carteasy cs = new Carteasy();
  data = cs.ViewAll(Context context);

  for (Map.Entry<Integer, Map> entry : data.entrySet()) {
     //get the Id
     Log.d("Key: ",entry.getKey());
     Log.d("Value: ",entry.getValue());

     //Get the items tied to the Id
     Map<String, String> innerdata = entry.getValue();
     for (Map.Entry<String, String> innerentry : innerdata.entrySet()) {
         Log.d("Inner Key: ",innerentry.getKey());
         Log.d("Inner Value: ",innerentry.getValue());
     }
  }
  ```

 *Viewing all items stored which is tied to an ID*

  ```
  Carteasy cs = new Carteasy();
  Map<String, String> data = cs.ViewData(String id, Context context);

  for (Map.Entry<String, String> entry : data.entrySet()) {
     //get the Id
     Log.d("Key: ",entry.getKey());
     Log.d("Value: ",entry.getValue());
  }
  ```

  *To persist data even when the app is closed, set persistData to True*

  ```
  Carteasy cs = new Carteasy();
  cs.persistData(Context context, boolean true);
  ```

  *To Stop persist data, , set persistData to False*

  ```
 Carteasy cs = new Carteasy();
 cs.persistData(Context context, boolean false);
 ```

 *Check isPersistEnabled*

 ```
 Carteasy cs = new Carteasy();
 cs.isPersistEnabled(Context context);
 ```

 *doesIDExistInCart*

 ```
 boolean value = cs.doesIDExistInCart(String id, Context context);
 ```

*Caveats*

Nothing here for now.



*Credits*

This library depends on json-simple-1.1.1



License
-------

```
Copyright (C) 2017 Tosin Onikute.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

	http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
