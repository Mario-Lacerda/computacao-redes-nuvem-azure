# Desafio Dio - Redes e Computação na Nuvem Azure



#### **Projeto ainda mais completo e abrangente com mais códigos para: Redes e Computação na Nuvem Azure**

**Introdução**

Este projeto irá guiá-lo pelos fundamentos das redes e da computação em nuvem no Microsoft Azure, uma plataforma de computação em nuvem que oferece uma ampla gama de serviços para ajudá-lo a construir, implantar e gerenciar seus aplicativos.



### **Pré-requisitos**



- Uma conta do Microsoft Azure

- O Visual Studio 2019 ou superior

- O .NET Core SDK 3.1 ou superior

  

### **Instruções**



1. **Crie um novo projeto do Visual Studio.**

2. **Selecione o modelo "Aplicativo Web do ASP.NET Core".**

3. **Nomeie o projeto como "AzureNetworkingInAction".**

4. **Clique em "Criar".**

   

5. #### Adicione os seguintes pacotes NuGet ao projeto:

   

   - Microsoft.Azure.Management.Network

   - Microsoft.Azure.Management.Compute

     

6. #### Adicione as seguintes classes ao projeto:

   

   - **VirtualNetworkService.cs:** Esta classe fornece métodos para interagir com o serviço de rede virtual do Azure.

   - **VirtualMachineService.cs:** Esta classe fornece métodos para interagir com o serviço de máquina virtual do Azure.

     

7. #### **Adicione o seguinte código ao arquivo "Startup.cs":**

   

csharp



```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton<IVirtualNetworkService, VirtualNetworkService>();
    services.AddSingleton<IVirtualMachineService, VirtualMachineService>();
}
```



1. #### **Adicione o seguinte código ao arquivo "Controllers/HomeController.cs":**

   

csharp



```csharp
public class HomeController : Controller
{
    private readonly IVirtualNetworkService _virtualNetworkService;
    private readonly IVirtualMachineService _virtualMachineService;

    public HomeController(IVirtualNetworkService virtualNetworkService, IVirtualMachineService virtualMachineService)
    {
        _virtualNetworkService = virtualNetworkService;
        _virtualMachineService = virtualMachineService;
    }

    public IActionResult Index()
    {
        return View();
    }

    [HttpPost]
    public async Task<IActionResult> CreateVirtualNetwork(string name, string addressSpace)
    {
        await _virtualNetworkService.CreateVirtualNetworkAsync(name, addressSpace);

        return RedirectToAction("Index");
    }

    [HttpPost]
    public async Task<IActionResult> CreateVirtualMachine(string name, string size, string image, string virtualNetworkName)
    {
        await _virtualMachineService.CreateVirtualMachineAsync(name, size, image, virtualNetworkName);

        return RedirectToAction("Index");
    }
}
```



1. #### **Execute o projeto.**

   

## **Conclusão**

Este projeto fornece uma base ainda mais sólida para você começar a construir redes e computação em nuvem no Microsoft Azure. Você pode usar os serviços de rede virtual e máquina virtual para criar e gerenciar redes virtuais, sub-redes, máquinas virtuais e outros recursos de rede.


