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

```csharp
// Exemplo: Classe e métodos em PascalCase, sendo a classe um substantivo e os métodos verbos
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

```csharp
//Quebrando a boa prática: Classe e métodos em camelCase, sendo a classe um adjetivo e os métodos substantivos
public class toDo_list
{
    // Tarefa adicionada à lista
    public void taskAdd(string taskName)
    {
        // Código para adicionar tarefa
    }

    // Tarefa marcada como concluída
    public void taskDone(int taskId)
    {
        // Código para marcar tarefa como concluída
    }

    // Tarefa removida da lista
    public void taskRemove(int taskId)
    {
        // Código para remover tarefa
    }
}
```

Neste exemplo, foi violada a boa prática "Use PascalCase para nomes de classes e métodos. Classes devem ser substantivos e métodos devem ser verbos", aplicando as más práticas a seguir:

- A classe "toDo_list" está em camelCase e deveria estar em PascalCase.
- A classe "toDo_list" é um adjetivo, deveria ser um substantivo.
- Os métodos "taskAdd", "taskDone" e "taskRemove" estão em camelCase, deveriam estar em PascalCase.
- Os métodos "taskAdd", "taskDone" e "taskRemove" são substantivos, deveriam ser verbos.




### 2.2. Parâmetros e Variáveis

Use camelCase para nomes de parâmetros e variáveis.

**Exemplo:**

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

    public void RemoveTask(int index)
    {
        _tasks.RemoveAt(index);
    }

    public void DisplayTasks()
    {
        for (int i = 0; i < _tasks.Count; i++)
        {
            Console.WriteLine($"{i + 1}. {_tasks[i]}");
        }
    }
}
```

### 2.3. Interfaces

As interfaces devem começar com 'I', como IProductRepository.

**Exemplo:**

```csharp
public interface IToDoRepository
{
    void AddTask(string task);
    void RemoveTask(int index);
    void DisplayTasks();
}

public class ToDoList : IToDoRepository
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

    public void RemoveTask(int index)
    {
        _tasks.RemoveAt(index);
    }

    public void DisplayTasks()
    {
        for (int i = 0; i < _tasks.Count; i++)
        {
            Console.WriteLine($"{i + 1}. {_tasks[i]}");
        }
    }
}
```

### 2.4. Clareza e Legibilidade

Evite abreviações ilegíveis e escolha nomes claros e descritivos para suas classes, métodos, variáveis e parâmetros.

**Exemplo:**

```csharp
public class Task
{
    public int Id { get; set; }
    public string Description { get; set; }
    public bool IsCompleted { get; set; }
}

public class ToDoList
{
    private List<Task> _tasks;

    public ToDoList()
    {
        _tasks = new List<Task>();
    }

    public void AddTask(Task task)
    {
        _tasks.Add(task);
    }

    public void RemoveTask(int id)
    {
        var taskToRemove = _tasks.FirstOrDefault(task => task.Id == id);
        if (taskToRemove != null)
        {
            _tasks.Remove(taskToRemove);
        }
    }

    public void DisplayTasks()
    {
        foreach (var task in _tasks)
        {
            Console.WriteLine($"{task.Id}. {task.Description} - {(task.IsCompleted ? "Completed" : "Not Completed")}");
        }
    }
}
```

**Exemplo de conta-regra:**

```csharp
public class Tsk
{
    public int i { get; set; }
    public string dscr { get; set; }
    public bool cmplt { get; set; }
}

public class TDL
{
    private List<Tsk> _tsks;

    public TDL()
    {
        _tsks = new List<Tsk>();
    }

    public void AddT(Tsk t)
    {
        _tsks.Add(t);
    }

    public void RmvT(int id)
    {
        var tRmv = _tsks.FirstOrDefault(t => t.i == id);
        if (tRmv != null)
        {
            _tsks.Remove(tRmv);
        }
    }

    public void DispT()
    {
        foreach (var t in _tsks)
        {
            Console.WriteLine($"{t.i}. {t.dscr} - {(t.cmplt ? "Cmpltd" : "NtCmpltd")}");
        }
    }
}
```

## 3. Funções e Métodos

### 3.1. Responsabilidade única

Cada função ou método deve ter apenas uma responsabilidade. Isso facilita a leitura, a manutenção e os testes do código.

**Exemplo:**

```csharp
public class Task
{
    public int Id { get; set; }
    public string Description { get; set; }
    public bool IsCompleted { get; set; }
}

public class ToDoList
{
    private List<Task> _tasks;

    public ToDoList()
    {
        _tasks = new List<Task>();
    }

    public void AddTask(Task task)
    {
        _tasks.Add(task);
    }

    public void RemoveTask(int taskId)
    {
        var taskToRemove = _tasks.FirstOrDefault(t => t.Id == taskId);
        if (taskToRemove != null)
        {
            _tasks.Remove(taskToRemove);
        }
    }

    public void DisplayTasks()
    {
        foreach (var task in _tasks)
        {
            Console.WriteLine($"{task.Id}. {task.Description} - {(task.IsCompleted ? "Completed" : "Not Completed")}");
        }
    }
}
```

**Exemplo de conta-regra:**

```csharp
public class Task
{
    public int Id { get; set; }
    public string Description { get; set; }
    public bool IsCompleted { get; set; }
}

public class ToDoList
{
    private List<Task> _tasks;

    public ToDoList()
    {
        _tasks = new List<Task>();
    }

    public void AddTaskAndDisplay(Task task)
    {
        _tasks.Add(task);
        
        foreach (var task in _tasks)
        {
            Console.WriteLine($"{task.Id}. {task.Description} - {(task.IsCompleted ? "Completed" : "Not Completed")}");
        }
    }

    public void RemoveTaskAndDisplay(int taskId)
    {
        var taskToRemove = _tasks.FirstOrDefault(t => t.Id == taskId);
        if (taskToRemove != null)
        {
            _tasks.Remove(taskToRemove);
        }

        foreach (var task in _tasks)
        {
            Console.WriteLine($"{task.Id}. {task.Description} - {(task.IsCompleted ? "Completed" : "Not Completed")}");
        }
    }
}

```

### 3.2. Orquestradores de métodos

Use orquestradores de métodos para coordenar a chamada de diversos métodos e executar uma operação complexa. Isso ajuda a manter o código modular e a separar as responsabilidades.

**Exemplo:**

```csharp
public class Task
{
    public int Id { get; set; }
    public string Description { get; set; }
    public bool IsCompleted { get; set; }
}

public interface ITaskRepository
{
    void AddTask(Task task);
    void RemoveTask(int taskId);
    IEnumerable<Task> GetAllTasks();
}

public class TaskRepository : ITaskRepository
{
    private List<Task> _tasks;

    public TaskRepository()
    {
        _tasks = new List<Task>();
    }

    public void AddTask(Task task)
    {
        _tasks.Add(task);
    }

    public void RemoveTask(int taskId)
    {
        var taskToRemove = _tasks.FirstOrDefault(t => t.Id == taskId);
        if (taskToRemove != null)
        {
            _tasks.Remove(taskToRemove);
        }
    }

    public IEnumerable<Task> GetAllTasks()
    {
        return _tasks;
    }
}

public class ToDoList
{
    private readonly ITaskRepository _taskRepository;

    public ToDoList(ITaskRepository taskRepository)
    {
        _taskRepository = taskRepository;
    }

    public void AddTask(Task task)
    {
        _taskRepository.AddTask(task);
    }

    public void RemoveTask(int taskId)
    {
        _taskRepository.RemoveTask(taskId);
    }

    public void DisplayTasks()
    {
        var tasks = _taskRepository.GetAllTasks();
        foreach (var task in tasks)
        {
            Console.WriteLine($"{task.Id}. {task.Description} - {(task.IsCompleted ? "Completed" : "Not Completed")}");
        }
    }
}

public class Program
{
    public static void Main()
    {
        var taskRepository = new TaskRepository();
        var toDoList = new ToDoList(taskRepository);

        var task1 = new Task { Id = 1, Description = "Beber café", IsCompleted = false };
        var task2 = new Task { Id = 2, Description = "Criar documento de Boas Práticas em .net para o IFA", IsCompleted = true };

        toDoList.AddTask(task1);
        toDoList.AddTask(task2);
        toDoList.DisplayTasks();
    }
}
```


### 3.3. Linguagem imperativa

Evite usar linguagem imperativa no código, que pode torná-lo difícil de entender e de manter. Em vez disso, prefira uma abordagem mais declarativa, que descreve o que deve ser feito em vez de como fazê-lo.

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
