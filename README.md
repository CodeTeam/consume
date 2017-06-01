Concept of queue wunderwaffle consumer.

==Consumer==

from ... import ConsumerFactory

consumers = [ConsumerFactory(tarantool_host='tnt:6666'),
             ConsumerFactory(rmq_host='ololo:666'), ]

Produced two consumers of the same type (by default it is that consumer pulls messages from queue, indefault behavior is to wait for push from queue). The main is first, if tarantool dies, second consumer starts to work.

Example given mentions factory, but it can be done with metaclass.



==Complete Hello World==
from ... import custom_migrate_command
from ... import TaskMeta, ResultMeta
from ... import ConsumerFactory
from ... import HandlerMeta
from ... import runserver
from handlers import CustomHandler

consumers = [ConsumerFactory(tarantool_host='tnt:6666'),
             ConsumerFactory(rmq_host='ololo:666'), ]

task = TaskMeta(**{'ololo': str, 'ololo': int, 'lolo': dict})
result = ResultMeta(**{'ololo': str, 'ololo': int, 'lolo': dict})

models = [task, result ]

handlers = [("/api/v1/lol", HandlerMeta(model_cls=task)), # оно родит тут класс, потому что торнадо нужен класс
            ("/api/v1/result", HandlerMeta(model_cls=result)),
            ('/api/v1/custom', CustomHandler)]

def custom_migrate_command():
    ...

runserver
