## setup
```
$ docker-compose run --rm server create_db
$ docker-compose up -d
```

open browser http://localhost:5000


## modify groups

```
$ docker-compose exec server bash
$ ./manage.py groups create sample-group
$ ./manage.py groups change_permissions --permissions 'create_dashboard' 3
```

ex) get_id
```
$ GROUP_NAME=sample-group
$ ./manage.py groups list | grep -B1 $GROUP_NAME | awk 'NR==1 {print $2}'
```


## Ref
DEFAULT_PERMISSIONS:
* create_dashboard
* create_query
* edit_dashboard
* edit_query
* view_query
* view_source
* execute_query
* list_users
* schedule_query
* list_dashboards
* list_alerts
* list_data_sources

```
# query-db, デフォルトのまま
./manage.py groups change_permissions --permissions 'create_dashboard,create_query,edit_dashboard,edit_query,view_query,view_source,execute_query,list_users,schedule_query,list_dashboards,list_alerts,list_data_sources' $GROUP_ID
```

```
# view-db, edit_queryを削除
./manage.py groups change_permissions --permissions 'create_dashboard,create_query,edit_dashboard,view_query,view_source,execute_query,list_users,schedule_query,list_dashboards,list_alerts,list_data_sources' $GROUP_ID
```
