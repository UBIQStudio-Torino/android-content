# android-content
## ExternalStoragePublicFileProvider
### Usage
1) Add the provider to your app manifest:
```xml
<manifest>
    ...
    <application>
        ...
        <provider
            android:name="com.ubiqstudio.ExternalStoragePublicFileProvider"
            android:authorities="com.example.fileprovider"
            android:exported="false"
            android:grantUriPermissions="true" />
        ...
    </application>
    ...
</manifest>
```
2) Get a content URI for the public file
```java
File storageDir = Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_PICTURES);
File photoFile = new File(storageDir, "photo.jpg");
Uri contentUri = ExternalStoragePublicFileProvider.getUriForFile("com.example.fileprovider", photoFile);
```
3) Use the content URI with ContentResolver
```java
context.getContentResolver().getType(contentUri)
context.getContentResolver().openInputStream(contentUri)
context.getContentResolver().methodThatRequiresContentURI(contentUri, ...)
```
