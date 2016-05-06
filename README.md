# long-poll

A Polymer element for updating documents using ETags.

Supply this element with a URL and a delay and it will check whether the Etag is the same as before,
firing an event if it's not. Your other elements can listen to this one and automatically know
to update when the source document's changed. It's kind of ghetto websockets, compatible with S3.

## Sample S3 CORS config

S3 needs to expose the ETag header for this to work. Here's an example CORS configuration:

```
<?xml version="1.0" encoding="UTF-8"?>
<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
    <CORSRule>
        <AllowedOrigin>*</AllowedOrigin>
        <AllowedMethod>GET</AllowedMethod>
        <MaxAgeSeconds>600</MaxAgeSeconds>
        <AllowedHeader>Authorization</AllowedHeader>
    </CORSRule>
    <CORSRule>
        <AllowedOrigin>*</AllowedOrigin>
        <AllowedMethod>HEAD</AllowedMethod>
        <MaxAgeSeconds>60</MaxAgeSeconds>
       <ExposeHeader>ETag</ExposeHeader>
    </CORSRule>
</CORSConfiguration>
```
