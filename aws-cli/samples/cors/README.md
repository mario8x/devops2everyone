## Cors (cross origin resource sharing)

http://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html

* create an s3 at 1 region (ex: us north)
upload file: samples/CORS/index.html,samples/CORS/error.html ( permission read for everyone)

* create an s3 at different region with above (ex: asia)

upload file: samples/CORS/loadpage.html ( permission read for everyone)
goto permission tab> Cors configuration:
add link of the s3 above to `AllowedOrigin`
`
<!-- Sample policy -->
<CORSConfiguration>
	<CORSRule>
		<AllowedOrigin>http://s3-static-web.s3-website-us-east-1.amazonaws.com</AllowedOrigin>
		<AllowedMethod>GET</AllowedMethod>
		<MaxAgeSeconds>3000</MaxAgeSeconds>
		<AllowedHeader>Authorization</AllowedHeader>
	</CORSRule>
</CORSConfiguration>
