# ng-admin-jwt-auth
Small module that allows to use JWT authentication with ng-admin.

Usage example:<br>
1) Include .js file to your index.html: 
2) Include module in your application:<br>
<pre> var app = angular.module('myApp', ['ng-admin', 'ng-admin.jwt-auth']);</pre>
3) Set full url to your authorization point: 
<pre>
    app.config(['NgAdminConfigurationProvider', 'RestangularProvider', 'ngAdminJWTAuthConfiguratorProvider', 
      function (NgAdminConfigurationProvider, RestangularProvider, <b>ngAdminJWTAuthConfigurator</b>) {
        var nga = NgAdminConfigurationProvider;
		    ngAdminJWTAuthConfigurator.setJWTAuthURL('http://localhost:3001/login');
        ...
</pre>

That's all, athorization configured!

API reference:
<ul>
  <li>
    setJWTAuthURL(fullUrl)
<pre>
ngAdminJWTAuthConfigurator.setJWTAuthURL('http://localhost:3001/login');
</pre>
  </li>
  <li>
    setCustomLoginTemplate(templateUrl):
<pre>
ngAdminJWTAuthConfigurator.setCustomLoginTemplate('customLoginTemplate.html');
</pre>
  </li>
    <li>
      <p>setCustomAuthHeader(obj) - configure custom headers. By defauls authorization header is 'Authorization' and field
      'Basic' adds for token. Final template of default authorization header is - Authorization: Basic {{token}}. You need to modify 
      token template and replace 'Basic' by 'Bearer'. Here is an example:
        
      </p>
      
<pre>
ngAdminJWTAuthConfigurator.setCustomAuthHeader({
	name: 'Authorization',
	template: 'Bearer {{token}}'
});

</pre>
  </li>
</ul>