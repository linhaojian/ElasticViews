# ElasticViews
Android views with touch Animation.

 
##Including in your project
####build.gradle
    compile 'com.github.skydoves:elasticviews:1.0.5'
    
####or Maven
```xml
<dependency>
  <groupId>com.github.skydoves</groupId>
  <artifactId>elasticviews</artifactId>
  <version>1.0.5</version>
</dependency>
```
    
##Usage
You can use like using normal views and you can give touch effect all of GroupViews very simply.

####Add XML Namespace
First add below XML Namespace inside your XML layout file.

```xml
xmlns:app="http://schemas.android.com/apk/res-auto"
```

####OnClick Method
All of ElasticViews need setOnClickListener - OnClick Method. If not, no Animation. 
```java
ElasticButton elasticButton = (ElasticButton)findViewById(R.id.elasticbutton);
        elasticButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // do something
            }
        });
```

or use butterknife
```java
@OnClick(R.id.elasticbutton)
    public void onClick(View v){
        // do something
    }
```

###ElasticButton
```xml
<com.github.skydoves.ElasticButton
        android:id="@+id/elasticbutton"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        app:button_backgroundColor="#30354b"
        app:button_round="20"
        app:button_scale="0.7"
        app:button_duration="400"
        app:button_labelText="Elastic Button"
        app:button_labelColor="#ffffff"
        app:button_labelSize="16"
        app:button_labelStyle="bold"/>
```

###ElasticButton use like TextView
If _button_backgroundColor_ attribute set as _@android:color/transparent_ <br>
you can use ElasticButton like TextView.
```xml
app:button_backgroundColor="@android:color/transparent"
```

###ElasticCheckButton
```xml
<com.github.skydoves.ElasticCheckButton
        android:id="@+id/elasticcheckbutton"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        app:checkbutton_backgroundColor="#30354b"
        app:checkbutton_round="30"
        app:checkbutton_scale="0.9"
        app:checkbutton_duration="400"
        app:checkbutton_labelText="Elastic CheckButton"
        app:checkbutton_labelColor="#ffffff"
        app:checkbutton_labelSize="16"
        app:checkbutton_labelStyle="bold"
        app:checkbutton_alpha="0.5"
        app:checkbutton_ischecked="false"/>
```

###ElasticImageView
```xml
<com.github.skydoves.ElasticImageView
            android:id="@+id/elasticimageview"
            android:layout_width="64dp"
            android:layout_height="64dp"
            android:scaleType="fitXY"
            android:src="@drawable/ic_question"
            app:imageview_duration="500"
            app:imageview_scale="0.7"/>
```

###ElasticFloatingButton
```xml
<com.github.skydoves.ElasticFloatingActionButton
            android:id="@+id/elasticfab"
            android:layout_width="64dp"
            android:layout_height="64dp"
            android:src="@drawable/ic_add"
            app:fabSize="normal"
            app:fabutton_duration="400"
            app:fabutton_scale="0.85"/>
```

###ElasticLayout
ElasticLayout don't animation for child views. 
If you want animation all of GroupViews, then use ElasticAction.
```xml
<com.github.skydoves.ElasticLayout
        android:id="@+id/elasticlayout"
        android:layout_width="match_parent"
        android:layout_height="80dp"
        app:layout_backgroundColor="#30354b"
        app:layout_duration="500"
        app:layout_scale="0.85">

        <TextView
            android:id="@+id/textView0"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="This is"
            android:textColor="#ffffff"
            android:textSize="18sp" />

        <TextView
            android:layout_below="@+id/textView1"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_alignParentBottom="true"
            android:text="ElasticLayout"
            android:textColor="#ffffff"
            android:textSize="18sp"
            android:gravity="end" />

    </com.github.skydoves.ElasticLayout>
```

###ElasticAction
you can give touch effect all of GroupViews very simply.<br>
```java
// argument : ViewGroup, Animation duration, scaleX, scaleY
ElasticAction.doAction((ViewGroup)anyViews, duration, 0.9f, 0.9f);
```

####Example : Normal Button
```java
@OnClick(R.id.button)
    public void addNewAlarm(View v){
        // ElasticAction : doAction
        ElasticAction.doAction((ViewGroup)v, 400, 0.85f, 0.85f); // argument : ViewGroup, duration, scaleX, scaleY

        // PostDelayed : delay duration time
        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                //Do something after duration time
            }
        }, 400);
    }
```

####Example : ListView Item
```java
private class ListViewItemClickListener implements AdapterView.OnItemClickListener{
        @Override
        public void onItemClick(AdapterView<?> adapterView, View clickedView, final int pos, long id)
        {
            // set your duration time
            int duration = 400;

            // ElasticAction : doAction
            ElasticAction.doAction((ViewGroup)clickedView, duration, 0.9f, 0.9f); // argument : ViewGroup, duration, scaleX, scaleY

            // PostDelayed : delay duration time
            new Handler().postDelayed(new Runnable() {
                @Override
                public void run() {
                    //Do something after duration time
                    Toast.makeText(getBaseContext(), "ListViewItem" + pos, Toast.LENGTH_SHORT).show();
                }
            }, duration);
        }
    };
```

#License
```xml
Copyright 2017 skydoves

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