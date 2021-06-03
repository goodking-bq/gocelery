# protocol 1
```py
task_message(
            headers={},
            properties={
                'correlation_id': task_id,
                'reply_to': reply_to or '',
            },
            body={
                'task': name,
                'id': task_id,
                'args': args,
                'kwargs': kwargs,
                'group': group_id,
                'group_index': group_index,
                'retries': retries,
                'eta': eta,
                'expires': expires,
                'utc': utc,
                'callbacks': callbacks,
                'errbacks': errbacks,
                'timelimit': (time_limit, soft_time_limit),
                'taskset': group_id,
                'chord': chord,
            },
            sent_event={
                'uuid': task_id,
                'name': name,
                'args': saferepr(args),
                'kwargs': saferepr(kwargs),
                'retries': retries,
                'eta': eta,
                'expires': expires,
            } if create_sent_event else None,
        )
 ```
 # protocol 2
 ```py
 task_message(
            headers={
                'lang': 'py',
                'task': name,
                'id': task_id,
                'shadow': shadow,
                'eta': eta,
                'expires': expires,
                'group': group_id,
                'group_index': group_index,
                'retries': retries,
                'timelimit': [time_limit, soft_time_limit],
                'root_id': root_id,
                'parent_id': parent_id,
                'argsrepr': argsrepr,
                'kwargsrepr': kwargsrepr,
                'origin': origin or anon_nodename(),
                'ignore_result': ignore_result,
            },
            properties={
                'correlation_id': task_id,
                'reply_to': reply_to or '',
            },
            body=(
                args, kwargs, {
                    'callbacks': callbacks,
                    'errbacks': errbacks,
                    'chain': chain,
                    'chord': chord,
                },
            ),
            sent_event={
                'uuid': task_id,
                'root_id': root_id,
                'parent_id': parent_id,
                'name': name,
                'args': argsrepr,
                'kwargs': kwargsrepr,
                'retries': retries,
                'eta': eta,
                'expires': expires,
            } if create_sent_event else None,
        )
```
