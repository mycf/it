```
spool flush.sql
select 'flushback table '|| original_name||' to before drop;' from user_recyclebin where type='TABLE'；
spool off
```

```
update fresh_busi_food
        <set>
            <trim prefix="sort_id = case food_id" suffix="end">
                <foreach collection="list" item="item" index="index">
                    when #{item.food_id} then #{index}
                </foreach>
            </trim>
        </set>
        <where>
            food_id in
            <trim prefix="(" suffixOverrides="," suffix=")">
                <foreach collection="list" item="item" index="index">
                    #{item.food_id},
                </foreach>
            </trim>
        </where>
```



