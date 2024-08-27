# require

## issues

### `ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)`

> ref: [mysql登陆报错](https://www.cnblogs.com/zhongyehai/p/10695334.html)
>
> > `$ mysql -uroot -p`  
> > 不输入密码  
> > `ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)` >> `$ mysql -uroot -p`  
> > 输入密码  
> > `ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)`
> >
> > ```sh
> > # Solution
> > $ sodu nvim /etc/mysql/my.cnf
> > add `[mysqld] skip-grant-tables`
> > # restart service
> > $ sudo service mysql stop
> > $ sudo service mysql start
> >
> > $ mysql
> > mysql> set password for 'root'@'localhost' = 'NewPassword';
> > mysql> flush privileges;
> > mysql> quit
> >
> > # comment skip-grant-tables
> >
> > $ sudo systemctl restart mysqld
> > ```
