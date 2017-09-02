# Decorators

Um decorator é uma forma prática e reusável de adicionarmos funcionalidades às nossas funções/métodos/classes, sem precisarmos alterar o código delas.

O decorator é um açúcar sintático que Python oferece aos desenvolvedores desde a versão 2.4, facilitando o desenvolvimento de códigos reusáveis.

```python
def time_this(original_function):      
    def new_function(*args,**kwargs):
        import datetime                 
        before = datetime.datetime.now()                     
        x = original_function(*args,**kwargs)                
        after = datetime.datetime.now()                      
        print("Elapsed Time = {0}".format(after-before))      
        return x                                             
    return new_function
  
@time_this
def func_a(stuff):
    import time
    time.sleep(3)
    return 20
    
func_a(1)
```

```python
def requires_permission(s_permission):                            
    def decorator(fn):                                            
        def decorated(*args,**kwargs):                            
            l_permissions = get_permissions(current_user_id())     
            if s_permission in l_permissions:                       
                return fn(*args,**kwargs)                         
            raise Exception("permission denied")                  
        return decorated                                          
    return decorator       
    
    
def get_permissions(i_user_id): #this is here so that the decorator doesn't throw NameErrors
    return ['logged_in',]

def current_user_id():        #ditto on the NameErrors
    return 1

#and now we can decorate stuff...                                     

@requires_permission('administrator')
def delete_user(i_user_id):
   """
   delete the user with the given Id. This function is only accessible to users with administrator permissions
   """

@requires_permission('logged_in')
def new_game():
    """
    any logged in user can start a new game
    """
    
@requires_permission('premium_member')
def premium_checkpoint():
   """
   save the game progress, only accessable to premium members
   """
    
delete_user()
new_game()
delete_user()
```



## Exercícios

1. Crie um decorator que imprime o nome da função decorada. Para exibir o nome da função utilize `__name__`.