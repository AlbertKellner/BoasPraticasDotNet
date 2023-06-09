# Boas Práticas de Programação em .NET: Nível Básico

## 1. Fundamentos

### 1.1. Siga as convenções

Siga as convenções estabelecidas pelo seu projeto ou equipe. Por exemplo, se o projeto usa constantes em maiúsculas e enumeradores com o prefixo 'E', siga esses padrões.

### 1.2. Regra do escoteiro

"Deixe sempre o acampamento mais limpo do que você encontrou!" O mesmo vale para o código. Faça check-in do código sempre melhor do que quando você o obteve. Se todos os desenvolvedores no time tiverem essa visão, o projeto evoluirá de forma mais saudável.

### 1.3. KISS

Mantenha as coisas simples! Siga o princípio "Keep It Simple, Stupid" (Mantenha isso simples e estúpido - KISS). Evite soluções complicadas quando uma abordagem simples e direta for suficiente.

### 1.4. Causa raiz

Procure sempre a causa raiz dos problemas e resolva-os completamente, em vez de aplicar soluções superficiais que possam levar a retrabalho.

### 1.5. Colaboração e comunicação

Trabalhe em colaboração com sua equipe e mantenha a comunicação aberta. Isso ajuda a garantir que todos estejam na mesma página e facilita a identificação e solução de problemas.

### 1.6. Testes automatizados

Escreva testes automatizados para validar a funcionalidade e a integridade do seu código. Testes bem escritos facilitam a detecção de problemas e aumentam a confiança na qualidade do software.

## 2. Padrão de Nomenclatura

### 2.1. Classes e Métodos

Use PascalCase para nomes de classes e métodos. Classes devem ser substantivos e métodos devem ser verbos.

Exemplo:
```csharp
public class ToDoList
{
    public void AddTask(string taskName)
    {
        // Código para adicionar tarefa
    }

    public void MarkTaskAsDone(int taskId)
    {
        // Código para marcar tarefa como concluída
    }

    public void RemoveTask(int taskId)
    {
        // Código para remover tarefa
    }
}

```

Quebrando a boa prática: Classe e métodos em camelCase, sendo a classe um adjetivo e os métodos substantivos
```csharp
public class toDoList
{
    public void add_task(string task)
    {
        // Código para adicionar a tarefa à lista.
    }

    public void remove_task(string task)
    {
        // Código para remover a tarefa da lista.
    }

    public void display_tasks()
    {
        // Código para exibir todas as tarefas da lista.
    }
}
```

Para seguir as recomendações de boas práticas, a classe e os métodos deveriam ser nomeados da seguinte forma:

- A classe deveria ser chamada `ToDoList` em vez de `toDoList`.
- O método `add_task` deveria ser chamado `AddTask`.
- O método `remove_task` deveria ser chamado `RemoveTask`.
- O método `display_tasks` deveria ser chamado `DisplayTasks`.

### 2.2. Parâmetros e Variáveis

Use camelCase para nomes de parâmetros e variáveis.

Exemplo:

```csharp
public class ToDoList
{
    public void AddTask(string taskName)
    {
        // Código para adicionar a tarefa à lista.
    }

    public void RemoveTask(string taskName)
    {
        // Código para remover a tarefa da lista.
    }

    public void DisplayTasks()
    {
        // Código para exibir todas as tarefas.
    }
}
```

Quebrando a boa prática: Nesta classe, quebramos a boa prática usando nomes pouco claros e não significativos para classes, métodos e variáveis.

```csharp
public class TDL
{
    public void AT(string tn)
    {
        // Código para adicionar a tarefa à lista.
    }

    public void RT(string tn)
    {
        // Código para remover a tarefa da lista.
    }

    public void DT()
    {
        // Código para exibir todas as tarefas.
    }
}
```

Veja o que foi feito de errado e como corrigir:

1. A classe `TDL` deve ser renomeada para `ToDoList` para tornar seu propósito mais claro.

2. O método `AT` deve ser renomeado para `AddTask`, e sua variável `tn` deve ser renomeada para `taskName`. Isso tornará a intenção do método e da variável mais fácil de entender.

3. O método `RT` deve ser renomeado para `RemoveTask`, e sua variável `tn` deve ser renomeada para `taskName`. Isso melhorará a legibilidade do método e da variável.

4. O método `DT` deve ser renomeado para `DisplayTasks`. Isso tornará a intenção do método mais clara.

Ao aplicar essas correções, estaríamos seguindo a boa prática 2.2 e tornando o código mais fácil de entender e manter.

### 2.3. Interfaces

As interfaces devem começar com 'I', como IProductRepository.

Exemplo:

```csharp
public interface ITodoList
{
    void AddTask(string taskName, string taskDescription);
    void RemoveTask(int taskId);
    void UpdateTaskStatus(int taskId, bool isCompleted);
}

public class TodoList : ITodoList
{
    private List<Task> tasks = new List<Task>();

    public void AddTask(string taskName, string taskDescription)
    {
        // Este método adiciona uma tarefa à lista de To-Do
    }

    public void RemoveTask(int taskId)
    {
        // Este método remove uma tarefa da lista de To-Do
    }

    public void UpdateTaskStatus(int taskId, bool isCompleted)
    {
        // Este método atualiza o status de uma tarefa na lista de To-Do
    }
}
```

Quebrando a boa prática: Iniciar nomes de interfaces com 'I'
```csharp
public interface TodoListInterface
{
    void AddTask(string taskName, string taskDescription);
    void RemoveTask(int taskId);
    void UpdateTaskStatus(int taskId, bool isCompleted);
}

public class TodoList : TodoListInterface
{
    private List<Task> tasks = new List<Task>();

    public void AddTask(string taskName, string taskDescription)
    {
        // Este método adiciona uma tarefa à lista de To-Do
    }

    public void RemoveTask(int taskId)
    {
        // Este método remove uma tarefa da lista de To-Do
    }

    public void UpdateTaskStatus(int taskId, bool isCompleted)
    {
        // Este método atualiza o status de uma tarefa na lista de To-Do
    }
}

```

No trecho de código acima, foi quebrada a boa prática 2.3, que recomenda iniciar os nomes das interfaces com a letra 'I'. A interface foi nomeada como `TodoListInterface` em vez de `ITodoList`. Para corrigir isso e seguir a recomendação de boas práticas, a interface deveria ser renomeada para `ITodoList`.

```csharp
public interface ITodoList
{
    // ...
}
```

### 2.4. Clareza e Legibilidade

Evite abreviações ilegíveis e escolha nomes claros e descritivos para suas classes, métodos, variáveis e parâmetros.

Exemplo:
```csharp
public class TodoList
{
    private List<Task> tasks = new List<Task>();

    public void AddTask(string taskName, string taskDescription)
    {
        Task newTask = new Task {
                                    Name = taskName, 
                                    Description = taskDescription, 
                                    IsCompleted = false 
                                };
        tasks.Add(newTask);
    }

    public void RemoveTask(int taskId)
    {
        Task taskToRemove = tasks.FirstOrDefault(t => t.Id == taskId);

        if (taskToRemove != null)
        {
            tasks.Remove(taskToRemove);
        }
    }

    public void UpdateTaskStatus(int taskId, bool isCompleted)
    {
        Task taskToUpdate = tasks.FirstOrDefault(t => t.Id == taskId);

        if (taskToUpdate != null)
        {
            taskToUpdate.IsCompleted = isCompleted;
        }
    }
}
```

Quebrando a boa prática:
```csharp
public class TDL
{
    private List<T> ts = new List<T>();

    public void AT(string tN, string tD)
    {
        T nT = new T { 
                        N = tN, 
                        D = tD, 
                        IC = false 
                     };
        ts.Add(nT);
    }

    public void RT(int tI)
    {
        T tR = ts.FirstOrDefault(t => t.I == tI);
        if (tR != null)
        {
            ts.Remove(tR);
        }
    }

    public void UTS(int tI, bool iC)
    {
        T tU = ts.FirstOrDefault(t => t.I == tI);
        if (tU != null)
        {
            tU.IC = iC;
        }
    }
}
```

No exemplo acima, o código foi escrito indo contra a boa prática, que foca na clareza e legibilidade. Aqui estão os tópicos sobre o que deveria ser feito para atender essas recomendações:

**Renomear a classe**: A classe `TDL` é uma abreviação ilegível, tornando difícil entender seu propósito. A classe deveria ser renomeada para `TodoList` para melhorar a legibilidade.

**Renomear os métodos**: Os nomes dos métodos `AT`, `RT` e `UT` são abreviações ilegíveis, tornando difícil entender o propósito de cada componente. Eles deveriam ser renomeados para `AddTask`, `RemoveTask` e `UpdateTask`, respectivamente.

**Usar nomes de variáveis mais descritivos**: As variáveis `t`, `ot` e `nt` nos métodos são abreviações que dificultam o entendimento do propósito de cada variável. As variáveis deveriam ser renomeadas para nomes mais descritivos, como `task`, `oldTask` e `newTask`.

## 3. Funções e Métodos

### 3.1. Responsabilidade única

Cada função ou método deve ter apenas uma responsabilidade. Isso facilita a leitura, a manutenção e os testes do código.

Exemplo: Cada método tem apenas uma responsabilidade
```csharp
public class ToDoList
{
    private List<string> _tasks;

    public ToDoList()
    {
        _tasks = new List<string>();
    }

    public void AddTask(string task)
    {
        _tasks.Add(task);
    }

    public void RemoveTask(string task)
    {
        string foundTask = _tasks.Find(t => t == task);

        if (foundTask != null)
        {
            _tasks.Remove(foundTask);
        }
    }

    public void CompleteTask(string task)
    {
        int taskIndex = _tasks.FindIndex(t => t == task);

        if (taskIndex != -1)
        {
            _tasks[taskIndex] = _tasks[taskIndex] + " (concluída)";
        }
    }
}
```

Quebrando a boa prática:
```csharp
public class ToDoList
{
    private List<string> _tasks;

    public ToDoList()
    {
        _tasks = new List<string>();
    }

    // Método para adicionar, remover ou marcar uma tarefa como concluída
    public void ManageTasks(string action, string task)
    {
        if (action == "add")
        {
            // Adiciona a tarefa à lista
            _tasks.Add(task);
        }
        else if (action == "remove")
        {
            // Remove a tarefa da lista
            string foundTask = _tasks.Find(t => t == task);

            if (foundTask != null)
            {
                _tasks.Remove(foundTask);
            }
        }
        else if (action == "complete")
        {
            // Marca a tarefa como concluída
            int taskIndex = _tasks.FindIndex(t => t == task);

            if (taskIndex != -1)
            {
                _tasks[taskIndex] = _tasks[taskIndex] + " (concluída)";
            }
        }
    }
}
```

Todo esse trecho de código foi contra as recomendações de boas práticas. O método `ManageTasks` possui múltiplas responsabilidades, ou seja, ele adiciona, remove e marca tarefas como concluídas. Isso vai contra a boa prática de Responsabilidade Única.

O que deveria ser feito para atender essas recomendações: Dividir o método `ManageTasks` em três métodos separados, cada um responsável por uma única ação.
- `AddTask`: para adicionar uma tarefa à lista.
- `RemoveTask`: para remover uma tarefa da lista.
- `CompleteTask`: para marcar uma tarefa como concluída.

Dessa forma, estaríamos seguindo a boa prática de Responsabilidade Única, garantindo que cada método tenha apenas uma responsabilidade, facilitando a leitura, manutenção e teste do código.

### 3.2. Orquestradores de métodos

Use orquestradores de métodos para coordenar a chamada de diversos métodos e executar uma operação complexa. Isso ajuda a manter o código modular e a separar as responsabilidades.

Neste exemplo, aplicamos a boa prática usando um método orquestrador `RegisterNewUser` para coordenar a chamada de diversos métodos e executar uma operação complexa. Os métodos não são do tipo void, e o orquestrador recebe e manipula os retornos de cada método anterior. Além disso, utilizamos variáveis implícitas para melhorar a legibilidade e a manutenção do código.

```csharp
public class UserRegistration
{
    public bool RegisterNewUser(User newUser)
    {
        var validationResult = ValidateUserData(newUser);

        if (validationResult.IsInvalid)
        {
            throw new InvalidOperationException($"Erro na validação de usuário.");
        }

        var userExists = UserExists(newUser);

        if (userExists)
        {
            throw new InvalidOperationException("Usuário já existe.");
        }

        var savedUser = SaveUser(newUser);

        var isEmailSent = SendWelcomeEmail(savedUser);

        var isEmailVerificationSent = SendEmailVerification(savedUser);

        return isEmailSent && isEmailVerificationSent;
    }

    private ValidationResult ValidateUserData(User user)
    {
        // Lógica de validação aqui
    }

    private bool UserExists(User user)
    {
        // Lógica de verificação aqui, chamando o repositorio
    }

    private User SaveUser(User user)
    {
        // Lógica de salvamento aqui, chamando o repositorio
    }

    private bool SendWelcomeEmail(User user)
    {
        // Lógica de envio de email aqui, chamando a infraestrutura
    }

    private bool SendEmailVerification(User user)
    {
        // Lógica de envio de email aqui, chamando a infraestrutura
    }
}
```

### 3.3. Linguagem imperativa

Evite usar linguagem imperativa no código, que pode torná-lo difícil de entender e de manter. Em vez disso, prefira uma abordagem mais declarativa, que descreve o que deve ser feito em vez de como fazê-lo.

Neste exemplo, em vez de usar loops e instruções condicionais imperativas para manipular a lista de tarefas, aplicamos uma abordagem mais declarativa usando métodos como Single e Where da biblioteca LINQ. Isso torna o código mais fácil de entender e manter.

```csharp
public class ToDoItem
{
    public int Id { get; set; }
    public string Description { get; set; }
    public bool IsDone { get; set; }
}

public class ToDoList
{
    private List<ToDoItem> _toDoItems;

    public ToDoList()
    {
        _toDoItems = new List<ToDoItem>();
    }

    public void AddItem(string taskDescription)
    {
        _toDoItems.Add(
            new ToDoItem 
                { 
                    Description = taskDescription, 
                    IsDone = false 
                });
    }

    public void MarkItemAsDone(int itemId)
    {
        _toDoItems
            .Single(item =>
                item.Id == itemId)
            .IsDone = true;
    }

    public IEnumerable<ToDoItem> GetPendingItems()
    {
        return _toDoItems
            .Where(item => !item.IsDone);
    }
}
```

Quebrando a boa prática: Usando linguagem imperativa no código em vez de uma abordagem declarativa

```csharp
public class ToDoItem
{
    public int Id { get; set; }
    public string Description { get; set; }
    public bool IsDone { get; set; }
}

public class ToDoList
{
    private List<ToDoItem> _toDoItems;

    public ToDoList()
    {
        _toDoItems = new List<ToDoItem>();
    }

    public void AddItem(string taskDescription)
    {
        var newItem = 
            new ToDoItem { 
                Description = taskDescription, 
                IsDone = false 
            };
        
        _toDoItems.Add(newItem);
    }

    public void MarkItemAsDone(int itemId)
    {
        foreach (var item in _toDoItems)
        {
            if (item.Id == itemId)
            {
                item.IsDone = true;
                break;
            }
        }
    }

    public List<ToDoItem> GetPendingItems()
    {
        var pendingItems = new List<ToDoItem>();

        foreach (var item in _toDoItems)
        {
            if (!item.IsDone)
            {
                pendingItems.Add(item);
            }
        }

        return pendingItems;
    }
}
```

No código acima, usamos linguagem imperativa, como loops e instruções condicionais, em vez de uma abordagem declarativa. Isso vai contra a boa prática mencionada.

Para melhorar o código e seguir as recomendações de boas práticas, podemos fazer o seguinte:

- Use a biblioteca `LINQ` para simplificar o código e torná-lo mais declarativo. Por exemplo, substitua o loop `foreach` no método `MarkItemAsDone` por um método `Single` da biblioteca `LINQ`.

- No método `GetPendingItems`, use o método `Where` da biblioteca `LINQ` em vez do loop `foreach` para filtrar os itens pendentes de maneira mais declarativa.

Ao aplicar essas recomendações, teremos um código mais fácil de entender e manter, seguindo a boa prática de evitar a linguagem imperativa e preferir uma abordagem mais declarativa.


### 3.4. Tamanho dos métodos

Mantenha os métodos curtos, com no máximo 40 ou 50 linhas. Se um método estiver ficando muito longo, considere refatorá-lo em métodos menores.

### 3.5. Declare variáveis próximas ao uso

Declare variáveis o mais próximo possível de onde elas serão usadas, para melhorar a legibilidade do código.

## 4. Comentários

### 4.1. Evite comentários redundantes

Não use comentários para explicar o que o código faz. Se o código não for claro, refatore-o para melhorar a legibilidade.

### 4.2. Não deixe comentários ou `TODO:` espalhados pelo código

Registre os débitos técnicos no backlog do projeto em vez de deixar comentários no código.

### 4.3. Use summary para documentar métodos

Use a tag `<summary>` para documentar métodos e suas funcionalidades.

## 5. Tratamento de Exceções

### 5.1. Use try-catch

Utilize blocos `try-catch` para tratar exceções e garantir que os recursos sejam liberados corretamente.

#### 5.1.1. Benefícios de try-catch

Os blocos `try-catch` permitem capturar e lidar com exceções de maneira apropriada, evitando que o programa encerre inesperadamente e garantindo que os recursos sejam liberados corretamente.

#### 5.1.2. Use o bloco finally

Utilize o bloco `finally` para executar ações de limpeza e garantir que os recursos sejam liberados, mesmo que uma exceção seja lançada. Isso ajuda a prevenir vazamentos de memória e outros problemas relacionados aos recursos.

### 5.2. Use using

O comando `using` pode ser usado para garantir que os objetos que implementam a interface `IDisposable` sejam liberados adequadamente.

#### 5.2.1. Benefícios do using

O `using` simplifica a liberação de recursos e garante que eles sejam liberados mesmo em caso de exceções, tornando o código mais seguro e fácil de manter.

### 5.3. Não engula exceções

Evite capturar exceções genéricas com um bloco `catch` vazio, pois isso pode ocultar erros e dificultar a depuração do código. Em vez disso, capture apenas as exceções específicas que você sabe como tratar.

### 5.4. Use exceções personalizadas

Crie classes de exceções personalizadas, estendendo a classe base `Exception`, quando precisar de exceções específicas para o domínio do seu aplicativo. Isso torna o código mais expressivo e fácil de entender.

### 5.5. Evite lançar exceções genéricas

Lance exceções específicas, em vez de exceções genéricas como `Exception`. Isso facilita a identificação e o tratamento adequado dos erros.

### 5.6. Registre informações de exceção

Registre informações de exceção, como mensagens e rastreamentos de pilha, em um sistema de log. Isso facilitará a depuração e análise de problemas no futuro.
