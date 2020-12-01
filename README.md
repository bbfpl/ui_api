# 路由
`UI::route('GET|POST|PUT|DELETE /path', [\module\demo\Index::class, 'index']);`

# mysql使用

**1,查询**

获取一条数据

`UI::DB('表名')->where($where)->row();`

获取所有数据

`UI::DB('表名')->where($where)->orderBy('id', 'DESC')->get();`

获取分页数据 $num=每页多少条数据 $page=当前第几页

`UI::DB('表名')->where($where)->orderBy('id', 'DESC')->paginate($num, $page);`

**2,添加**

```php
$id = UI::DB('表名')->insertGetLastId($data);
var_dump($id); //返回插入数据的id
```

**3,更新**

`UI::DB('表名')->where($where)->update($update_data);`

**4,删除**

`UI::DB('表名')->where($where)->delete();`

#  request

获取提交数据
不管提交post还是get都是用input来获取数据
比如 前端提交的数据是
```json
{
    name:'张三',
    age:10
}
```

**1,获取**
```php
    $name = input('name');
    var_dump($name); //张三

```
#  config配置文件

**1,设置**

```php
// set 获取需要设置的内容
UI::config()->set('config.mysql', [
    'host' => 'localhost',
    'port' => '3306',
    'user' => 'root',
    'password' => 'root',
]);
// 保存
UI::config()->sync('config');
// 保存文件在tmp/config.php文件
```


**2,获取**

```php
$config = UI::config()->get('config.mysql');
var_dump($config);
```



