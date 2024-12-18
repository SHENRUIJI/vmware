-- 连接到您的数据库
\c your_database_name;

-- 授予对 public schema 的所有权限给特定用户
GRANT ALL ON SCHEMA public TO your_username;

-- 授予对所有现有表格的 SELECT, INSERT, UPDATE, DELETE 权限给特定用户
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO your_username;

-- 对未来创建的新表格自动赋予相同的权限
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO your_username;

-- 对于序列（通常用于自增字段），也应设置相应的权限
GRANT USAGE, SELECT ON ALL SEQUENCES IN SCHEMA public TO your_username;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT USAGE, SELECT ON SEQUENCES TO your_username;

-- 对函数也需要设置权限
GRANT EXECUTE ON ALL FUNCTIONS IN SCHEMA public TO your_username;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT EXECUTE ON FUNCTIONS TO your_username;
