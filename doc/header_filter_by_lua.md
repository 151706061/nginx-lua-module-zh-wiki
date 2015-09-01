header_filter_by_lua
---------------

**�﷨:** *header_filter_by_lua &lt;lua-script-str&gt;*

**����:** *http, server, location, location if*

**nginxִ�н׶�:** *output-header-filter*

��`<lua-script-str>`�е�lua���룬������Ӧ����Ϣ��ͷ����Ϣ��

ע�⣬���еĽӿں��������ִ�н׶���ʧЧ�ģ�

- ����ຯ��������ngx.say��ngx.send_headers��

- �����ຯ��(����ngx.redirect��ngx.exec)

- ��������غ��� ������ngx.location.capture��ngx.location.capture_multi��

- �׽����ຯ��������ngx.socket.tcp��ngx.req.socket��

�����������չʾ���ǣ���header_filter_by_lua�׶���,�ὫӦ����Ϣͷ���е�ĳ�����ֶθ��ǵ������û������ֶΣ����ǽ�����ӽ�ͷ����

```nginx

 location / {
	 proxy_pass http://mybackend;
	 header_filter_by_lua 'ngx.header.Foo = "blah"';
 }

```

���ָ����������ڰ汾 `v0.2.1rc20 �С�

[����Ŀ¼](#directives)


> English Source

**syntax:** *header_filter_by_lua &lt;lua-script-str&gt;*

**context:** *http, server, location, location if*

**phase:** *output-header-filter*

Uses Lua code specified in `<lua-script-str>` to define an output header filter.

Note that the following API functions are currently disabled within this context:

- Output API functions (e.g., ngx.say and ngx.send_headers)

- Control API functions (e.g., ngx.redirect and ngx.exec)

- Subrequest API functions (e.g., ngx.location.capture and ngx.location.capture_multi)

- Cosocket API functions (e.g., ngx.socket.tcp and ngx.req.socket).

Here is an example of overriding a response header (or adding one if absent) in our Lua header filter:

```nginx
    location / {
        proxy_pass http://mybackend;
        header_filter_by_lua 'ngx.header.Foo = "blah"';
    }
```nginx

This directive was first introduced in the v0.2.1rc20 release.

[BACK TO TOC](#directives)
