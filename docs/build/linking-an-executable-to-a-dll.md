---
title: Vincular un ejecutable a un archivo DLL
ms.date: 08/22/2019
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
ms.openlocfilehash: 2f907fedcaaf9897749ee0eb6a7ea5a33e1af679
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422839"
---
# <a name="link-an-executable-to-a-dll"></a>Vincular un ejecutable a un archivo DLL

Un archivo ejecutable vincula (o carga) una DLL de una de las dos maneras siguientes:

- *Vinculación implícita*, donde el sistema operativo carga el archivo DLL al mismo tiempo que el ejecutable que lo usa. El ejecutable del cliente llama a las funciones exportadas del archivo DLL de la misma manera que si las funciones estuviesen vinculadas de forma estática e incluyeran el ejecutable. En ocasiones, la vinculación implícita se conoce como *carga estática* o *vinculación dinámica en tiempo de carga*.

- *Vinculación explícita*, donde el sistema operativo carga el archivo DLL a petición en tiempo de ejecución. Un archivo ejecutable que usa un archivo DLL mediante vinculación explícita debe cargar y descargar explícitamente el archivo DLL. También debe configurar un puntero de función para acceder desde el archivo DLL a todas las funciones que usa. A diferencia de las llamadas a funciones en una biblioteca vinculada estáticamente o un archivo DLL vinculado implícitamente, el archivo ejecutable del cliente debe llamar a las funciones exportadas de un archivo DLL vinculado explícitamente a través de punteros a función. En ocasiones, la vinculación explícita se conoce como *carga dinámica* o *vinculación dinámica en tiempo de ejecución*.

Un ejecutable puede usar cualquier método de vinculación para vincular al mismo archivo DLL. Además, estos métodos no son mutuamente excluyentes; un archivo ejecutable se puede vincular de forma implícita a un archivo DLL y otro se le podría asociar de forma explícita.

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>Determinar el método de vinculación que se debe utilizar

El uso de la vinculación implícita o la vinculación explícita es una decisión arquitectónica que debe tomar para la aplicación. Cada método ofrece ventajas y desventajas.

### <a name="implicit-linking"></a>Vinculación implícita

La vinculación implícita se produce cuando el código de una aplicación llama a una función DLL exportada. Cuando se compila o ensambla el código fuente para el archivo ejecutable de llamada, la llamada a la función del archivo DLL genera una referencia de función externa en el código objeto. Para resolver esta referencia externa, la aplicación debe vincularse a la biblioteca de importación (archivo .LIB) proporcionada por el autor del archivo DLL.

La biblioteca de importación sólo contiene código para cargar el archivo DLL e implementar llamadas a las funciones del archivo DLL. Cuando se encuentra una función externa en una biblioteca de importación, se notifica al vinculador que el código de la función está en un archivo DLL. Para resolver referencias externas a archivos DLL, el vinculador simplemente agregará información al archivo ejecutable para indicar al sistema dónde se encuentra el código del archivo DLL cuando se inicie el proceso.

Cuando el sistema inicia un programa que contiene referencias vinculadas dinámicamente, utiliza esta información en el archivo ejecutable del programa para encontrar los archivos DLL necesarios. Si no encuentra el archivo DLL, el sistema finalizará el proceso y mostrará un cuadro de diálogo para notificar el error. En caso contrario, el sistema asigna los módulos de DLL al espacio de direcciones del proceso.

Si alguno de los archivos DLL tiene una función de punto de entrada para el código de inicialización y finalización como `DllMain`, el sistema operativo llama a la función. Uno de los parámetros pasados a la función de punto de entrada especifica un código que indica que se está asociando el archivo DLL al proceso. Si la función de punto de entrada no devuelve TRUE, el sistema finaliza el proceso y notifica un error.

Por último, el sistema modifica el código ejecutable del proceso para proporcionar direcciones de inicio a las funciones del archivo DLL.

Como el resto del código de un programa, el cargador asigna el código de DLL al espacio de direcciones del proceso cuando este se inicia. El sistema operativo solo lo carga en memoria cuando es necesario. Como resultado, los atributos de código `PRELOAD` y `LOADONCALL` que usan los archivos .def para controlar la carga en las versiones anteriores de Windows ya no tienen sentido.

### <a name="explicit-linking"></a>Vinculación explícita

La mayoría de las aplicaciones usan la vinculación implícita, ya que es el método de vinculación más sencillo de utilizar. Pero en ocasiones es necesario usar la vinculación explícita. Algunas de las razones más frecuentes para utilizar la vinculación explícita son:

- La aplicación no conoce el nombre de un archivo DLL que carga hasta el tiempo de ejecución. Por ejemplo, es posible que la aplicación obtenga el nombre del archivo DLL y las funciones exportadas de un archivo de configuración durante el inicio.

- El sistema operativo finaliza un proceso que usa la vinculación implícita si no se encuentra el archivo DLL al iniciar el proceso. En esta situación, un proceso que use la vinculación explícita no finaliza y puede intentar recuperarse del error. Por ejemplo, podría notificar el error al usuario y pedirle que especifique otra ruta de acceso al archivo DLL.

- Un proceso que use la vinculación implícita también finaliza si cualquiera de los archivos DLL a los que está vinculado incluye una función `DllMain` que produce errores. Un proceso que use la vinculación explícita no finaliza en esta situación.

- Una aplicación que se vincule implícitamente a muchos archivos DLL puede resultar lenta de inicializar, puesto que Windows cargará todos los archivos DLL cuando se cargue la aplicación. Para mejorar el rendimiento de inicio, es posible que una aplicación solo use la vinculación implícita para los archivos DLL necesarios inmediatamente después de la carga. Podría usar la vinculación explícita para cargar otros archivos DLL solo cuando sea necesario.

- La vinculación explícita elimina la necesidad de vincular la aplicación mediante una biblioteca de importación. Si los cambios en el archivo DLL modifican los ordinales de exportación, las aplicaciones no tienen que volver a vincularse si llaman a `GetProcAddress` con el nombre de una función y no un valor ordinal. Las aplicaciones que usan la vinculación implícita todavía deben volver a vincularse a la biblioteca de importación modificada.

Hay que tener en cuenta dos posibles peligros en la vinculación explícita:

- Si el archivo DLL tiene una función de punto de entrada `DllMain`, el sistema operativo llamará a la función en el contexto del subproceso que ha llamado a `LoadLibrary`. No se llamará a la función de punto de entrada si el archivo DLL ya está asociado al proceso debido a una llamada anterior a `LoadLibrary` sin una llamada correspondiente a la función `FreeLibrary`. La vinculación explícita puede producir problemas si el archivo DLL usa una función `DllMain` para inicializar cada subproceso de un proceso, porque los subprocesos que ya existen cuando se llama a `LoadLibrary` (o `AfxLoadLibrary`) no se inicializan.

- Si un archivo DLL declara datos de extensión estática como `__declspec(thread)`, se puede producir un error de protección si se vincula explícitamente. Después de cargar el archivo DLL mediante una llamada a `LoadLibrary`, se producirá un error de protección siempre que el código haga referencia a estos datos. (Entre los datos de extensión estática se incluyen elementos estáticos globales y locales). Por eso, cuando se crea un archivo DLL, se debe evitar el uso de almacenamiento local para el subproceso. Si no es posible, informe a los usuarios del archivo DLL de los posibles problemas de carga dinámica del archivo DLL. Para obtener más información, vea [Uso de almacenamiento local para el subproceso en una biblioteca de vínculos dinámicos (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>Procedimiento para usar la vinculación implícita

Para usar un archivo DLL mediante la vinculación implícita, los ejecutables de cliente deben obtener estos archivos del proveedor del archivo DLL:

- Uno o más archivos de encabezado (archivos .h) con las declaraciones de los datos, las funciones y las clases de C++ exportadas en el archivo DLL. Las clases, las funciones y los datos exportados por el archivo DLL deben estar marcados como `__declspec(dllimport)` en el archivo de encabezado. Para obtener más información, consulte [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Biblioteca de importación que se va a vincular al archivo ejecutable. El enlazador crea la biblioteca de importación cuando se compila el archivo DLL. Para obtener más información, vea [Archivos LIB como entrada del enlazador](reference/dot-lib-files-as-linker-input.md).

- El propio archivo DLL.

Para usar los datos, las funciones y las clases de un archivo DLL mediante la vinculación implícita, cualquier archivo de origen de cliente debe incluir los archivos de encabezado en los que se declaran. Desde una perspectiva de programación, las llamadas a las funciones exportadas son como cualquier otra llamada de función.

Para compilar el archivo ejecutable cliente, tiene que vincularlo a la biblioteca de importación del archivo DLL. Si usa un archivo Make externo o un sistema de compilación, especifique la biblioteca de importación junto con los demás archivos de objeto o bibliotecas que vincule.

El sistema operativo deberá ser capaz de encontrar el archivo DLL cuando cargue el archivo ejecutable de llamada. Esto significa que debe implementar o comprobar la existencia del archivo DLL al instalar la aplicación.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Procedimiento para vincular explícitamente a un archivo DLL

Para usar un archivo DLL con la vinculación explícita, las aplicaciones deben realizar una llamada de función para cargar explícitamente el archivo DLL en tiempo de ejecución. Para una vinculación explícita a un archivo DLL, una aplicación debe:

- Llamar a [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) o a una función similar para cargar el archivo DLL y obtener un identificador de módulo.

- Llamar a [GetProcAddress](getprocaddress.md) para obtener un puntero a función para cada función exportada a la que la aplicación llama. Como las aplicaciones llaman a las funciones de DLL mediante un puntero, el compilador no genera referencias externas, por lo que no hay necesidad de vincular a una biblioteca de importación. Pero debe tener una instrucción `typedef` o `using` que defina la firma de llamada de las funciones exportadas a las que llama.

- Llamar a [FreeLibrary](freelibrary-and-afxfreelibrary.md) cuando se haya terminado de usar el archivo DLL.

Por ejemplo, esta función de ejemplo llama a `LoadLibrary` para cargar un archivo DLL denominado "MyDLL", llama a `GetProcAddress` para obtener un puntero a una función denominada "DLLFunc1", llama a la función y guarda el resultado y, después, llama a `FreeLibrary` para descargar el archivo DLL.

```C
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)
{
    HINSTANCE hDLL;               // Handle to DLL
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
    HRESULT hrReturnVal;

    hDLL = LoadLibrary("MyDLL");
    if (NULL != hDLL)
    {
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");
        if (NULL != lpfnDllFunc1)
        {
            // call the function
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);
        }
        else
        {
            // report the error
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }
    return hrReturnVal;
}
```

A diferencia de este ejemplo, en la mayoría de los casos se debe llamar a `LoadLibrary` y `FreeLibrary` solo una vez en la aplicación para un archivo DLL determinado, en especial si se va a llamar a varias funciones en el archivo DLL o a funciones DLL repetidamente.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Trabajar con bibliotecas de importación y archivos de exportación](reference/working-with-import-libraries-and-export-files.md)

- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
