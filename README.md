# laravel-question


#跨域这是直接注册到全局路由中options---（返回post接口数据需要设置header头）

        $app->middleware([
            App\Http\Middleware\CorsMiddleware::class
        ]);
        
        $app->routeMiddleware([
         //'Cors' => App\Http\Middleware\CorsMiddleware::class,
         'AdminMenu' => App\Http\Middleware\Admin\AdminMenuMiddleware::class,
         'CheckTokenCenterServer' => App\Http\Middleware\CheckTokenCenterServerMiddleware::class,
         'CheckCompany' => App\Http\Middleware\CheckCompanyMiddleware::class,
         'RouterPermission' => App\Http\Middleware\RouterPermissionMiddleware::class,
        ]);


       if ($request->getMethod() === 'OPTIONS') {
            $response = new Response('OK', 200);
            $response->header('Access-Control-Allow-Origin', '*');
            $response->header('Access-Control-Allow-Methods', 'GET,POST,PUT,PATCH,DELETE,OPTIONS');
            $response->header('Access-Control-Allow-Credentials', 'true');
            $response->header('Access-Control-Allow-Headers', 'X-Token,X-Auth,X-Cid');
            return $response;
        }else{
            $response = $next($request);
        }
        return $response;
        
 
 
 #返回结果需要设置header
 
        header("Access-Control-Allow-Origin:*");
        header("Access-Control-Allow-Headers: X-Token,X-Cid,X-Auth");

     
