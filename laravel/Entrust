### Create Role

	$admin = new Role();
	$admin->name         = 'admin';
	$admin->display_name = 'User Administrator'; // optional
	$admin->description  = 'User is allowed to manage and edit other users'; // optional
	$admin->save();

### Attack Role To User
	$user->attachRole($admin);

### Create Permission
	$createPost = new Permission();
	$createPost->name         = 'create-post';
	$createPost->display_name = 'Create Posts'; // optional
	$createPost->description  = 'create new blog posts'; // optional
	
### Attack Permission to Role
	
	$admin->attachPermission($createPost);
	$owner->attachPermissions(array($createPost, $editUser));
	
#### Checking for Roles & Permissions
	$user->hasRole('owner');   // false
	$user->can('create-post'); // true
	$user->hasRole(['owner', 'admin']);       // true
	$user->can(['edit-user', 'create-post']); // true

> By default, if any of the roles or permissions are present for a user then the method will return true. Passing `true` as a second parameter instructs the method to require **all** of the items:

The  `Entrust`  class has shortcuts to both  `can()`  and  `hasRole()`  for the currently logged in user:

    Entrust::hasRole('role-name');
    Entrust::can('permission-name');
    // is identical to
    Auth::user()->hasRole('role-name');
    Auth::user()->can('permission-name')

### Middleware
	Route::group(['prefix' => 'admin', 'middleware' => ['role:admin']], function() {
	 Route::get('/', 'AdminController@welcome');
	 Route::get('/manage', ['middleware' => ['permission:manage-admins'], 'uses' => 'AdminController@manageAdmins']);
	});
	// AND / OR
	'middleware' => ['role:admin|root']
	'middleware' => ['role:owner', 'role:writer']
> Written with [StackEdit](https://stackedit.io/).
