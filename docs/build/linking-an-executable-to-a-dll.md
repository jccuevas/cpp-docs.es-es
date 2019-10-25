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
ms.openlocfilehash: fe0a4fc37291b4ccc904f889a9d38748fc38195c
ms.sourcegitcommit: ec524d1f87bcce2b26b02e6d297f42c94b3db36e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026006"
---
# <a name="link-an-executable-to-a-dll"></a>Vincular un ejecutable a un archivo DLL

Un archivo ejecutable vincula (o carga) una DLL de una de las dos maneras siguientes:

- *Vinculación implícita*, donde el sistema operativo carga el archivo dll al mismo tiempo que el ejecutable que lo usa. El ejecutable del cliente llama a las funciones exportadas del archivo DLL de la misma manera que si las funciones estuviesen vinculadas estáticamente y contenían el ejecutable. La vinculación implícita a veces se conoce como *carga estática* o *vinculación dinámica en tiempo de carga*.

- *Vinculación explícita*, donde el sistema operativo carga el archivo DLL a petición en tiempo de ejecución. Un archivo ejecutable que utiliza un archivo DLL mediante vinculación explícita debe cargar y descargar explícitamente el archivo DLL. También debe configurar un puntero de función para tener acceso a cada función que usa desde el archivo DLL. A diferencia de las llamadas a funciones en una biblioteca vinculada estáticamente o un archivo DLL vinculado implícitamente, el archivo ejecutable del cliente debe llamar a las funciones exportadas de un archivo DLL vinculado explícitamente a través de punteros a función. La vinculación explícita se denomina a veces *carga dinámica* o *vinculación dinámica en tiempo de ejecución*.

Un ejecutable puede usar cualquier método de vinculación para vincular al mismo archivo DLL. Además, estos métodos no son mutuamente excluyentes; un archivo ejecutable puede vincularse implícitamente a un archivo DLL y otro puede asociarse explícitamente a él.

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>Determinar el método de vinculación que se debe utilizar

El uso de la vinculación implícita o la vinculación explícita es una decisión arquitectónica que debe tomar para su aplicación. Cada método tiene ventajas y desventajas.

### <a name="implicit-linking"></a>Vinculación implícita

La vinculación implícita se produce cuando el código de una aplicación llama a una función de DLL exportada. Cuando se compila o ensambla el código fuente para el archivo ejecutable de llamada, la llamada a la función del archivo DLL genera una referencia de función externa en el código objeto. Para resolver esta referencia externa, la aplicación debe vincularse a la biblioteca de importación (archivo .LIB) proporcionada por el autor del archivo DLL.

La biblioteca de importación sólo contiene código para cargar el archivo DLL e implementar llamadas a las funciones del archivo DLL. Cuando se encuentra una función externa en una biblioteca de importación, se notifica al vinculador que el código de la función está en un archivo DLL. Para resolver referencias externas a archivos DLL, el vinculador simplemente agregará información al archivo ejecutable para indicar al sistema dónde se encuentra el código del archivo DLL cuando se inicie el proceso.

Cuando el sistema inicia un programa que contiene referencias vinculadas dinámicamente, utiliza esta información en el archivo ejecutable del programa para encontrar los archivos DLL necesarios. Si no encuentra el archivo DLL, el sistema finaliza el proceso y muestra un cuadro de diálogo que informa del error. De lo contrario, el sistema asigna los módulos DLL en el espacio de direcciones de proceso.

Si alguno de los archivos dll tiene una función de punto de entrada para el código de inicialización y finalización como `DllMain`, el sistema operativo llama a la función. Uno de los parámetros pasados a la función de punto de entrada especifica un código que indica que se está asociando el archivo DLL al proceso. Si la función de punto de entrada no devuelve TRUE, el sistema finaliza el proceso y notifica el error.

Por último, el sistema modifica el código ejecutable del proceso para proporcionar direcciones de inicio a las funciones del archivo DLL.

Al igual que el resto del código de un programa, el cargador asigna código DLL en el espacio de direcciones del proceso cuando se inicia el proceso. El sistema operativo lo carga en la memoria solo cuando sea necesario. Como resultado, los atributos `PRELOAD` de `LOADONCALL` código y utilizados por los archivos. def para controlar la carga en versiones anteriores de Windows ya no tienen significado.

### <a name="explicit-linking"></a>Vinculación explícita

La mayoría de las aplicaciones usan la vinculación implícita porque es el método de vinculación más fácil de usar. Sin embargo, hay ocasiones en las que es necesaria la vinculación explícita. Algunas de las razones más frecuentes para utilizar la vinculación explícita son:

- La aplicación no conoce el nombre de un archivo DLL que se carga hasta el tiempo de ejecución. Por ejemplo, la aplicación podría obtener el nombre de la DLL y las funciones exportadas de un archivo de configuración en el inicio.

- El sistema operativo finaliza un proceso que usa la vinculación implícita si la DLL no se encuentra en el inicio del proceso. Un proceso que usa la vinculación explícita no finaliza en esta situación y puede intentar recuperarse del error. Por ejemplo, podría notificar el error al usuario y pedirle que especifique otra ruta de acceso al archivo DLL.

- Un proceso que usa la vinculación implícita también se termina si cualquiera de los archivos DLL a los que `DllMain` está vinculado tiene una función que produce un error. En esta situación no se finaliza un proceso que usa la vinculación explícita.

- Una aplicación que se vincule implícitamente a muchos archivos DLL puede resultar lenta de inicializar, puesto que Windows cargará todos los archivos DLL cuando se cargue la aplicación. Para mejorar el rendimiento de inicio, una aplicación podría usar solo la vinculación implícita para los archivos dll necesarios inmediatamente después de la carga. Podría usar la vinculación explícita para cargar otros archivos dll solo cuando sea necesario.

- La vinculación explícita elimina la necesidad de vincular la aplicación mediante una biblioteca de importación. Si los cambios en el archivo dll hacen que los ordinales de exportación cambien, las aplicaciones no tienen que `GetProcAddress` volver a vincularse si llaman a usando el nombre de una función y no un valor ordinal. Las aplicaciones que usan la vinculación implícita todavía deben volver a vincularse a la biblioteca de importación modificada.

Hay que tener en cuenta dos posibles peligros en la vinculación explícita:

- Si el archivo dll tiene `DllMain` una función de punto de entrada, el sistema operativo llama a la función en el contexto del `LoadLibrary`subproceso que llamó a. No se llama a la función de punto de entrada si el archivo DLL ya está asociado al proceso debido a una `LoadLibrary` llamada anterior a que no ha tenido una `FreeLibrary` llamada correspondiente a la función. La vinculación explícita puede producir problemas si el archivo `DllMain` dll usa una función para inicializar cada subproceso de un proceso, porque los `LoadLibrary` subprocesos que ya existen cuando se llama a (o `AfxLoadLibrary`) no se inicializan.

- Si un archivo dll declara datos de extensión estática como `__declspec(thread)`, puede producirse un error de protección si se vincula explícitamente. Una vez que se carga el archivo DLL mediante `LoadLibrary`una llamada a, se produce un error de protección cada vez que el código hace referencia a estos datos. Entre los datos de extensión estática se incluyen elementos estáticos globales y locales. Por eso, cuando se crea un archivo DLL, debe evitarse el uso de almacenamiento local de subprocesos. Si no es posible, informe a los usuarios del archivo DLL de los posibles problemas de carga dinámica del archivo DLL. Para obtener más información, vea [usar el almacenamiento local para el subproceso en una biblioteca de vínculos dinámicos (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>Cómo usar la vinculación implícita

Para usar un archivo DLL mediante la vinculación implícita, los ejecutables de cliente deben obtener estos archivos del proveedor de la DLL:

- Uno o más archivos de encabezado (archivos. h) que contienen las declaraciones de los datos, las funciones y C++ las clases exportadas en el archivo dll. Las clases, las funciones y los datos exportados por el archivo dll `__declspec(dllimport)` deben estar marcados en el archivo de encabezado. Para obtener más información, consulte [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Biblioteca de importación que se va a vincular al archivo ejecutable. El vinculador crea la biblioteca de importación cuando se compila el archivo DLL. Para obtener más información, vea [archivos lib como entrada del vinculador](reference/dot-lib-files-as-linker-input.md).

- El archivo DLL real.

Para usar los datos, las funciones y las clases de un archivo DLL mediante la vinculación implícita, cualquier archivo de origen de cliente debe incluir los archivos de encabezado que los declaran. Desde una perspectiva de codificación, las llamadas a las funciones exportadas son como cualquier otra llamada de función.

Para compilar el archivo ejecutable del cliente, debe vincular con la biblioteca de importación del archivo DLL. Si usa un archivo make externo o un sistema de compilación, especifique la biblioteca de importación junto con los demás archivos de objeto o bibliotecas que vincule.

El sistema operativo deberá ser capaz de encontrar el archivo DLL cuando cargue el archivo ejecutable de llamada. Esto significa que debe implementar o comprobar la existencia de la DLL al instalar la aplicación.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Cómo vincular explícitamente a un archivo DLL

Para usar un archivo DLL mediante vinculación explícita, las aplicaciones deben realizar una llamada de función para cargar explícitamente el archivo DLL en tiempo de ejecución. Para una vinculación explícita a un archivo DLL, una aplicación debe:

- Llame a [LoadLibrary](loadlibrary-and-afxloadlibrary.md), `LoadLibraryEx` o una función similar para cargar el archivo dll y obtener un identificador de módulo.

- Llame a [GetProcAddress](getprocaddress.md) para obtener un puntero de función a cada función exportada a la que llama la aplicación. Dado que las aplicaciones llaman a las funciones de DLL a través de un puntero, el compilador no genera referencias externas, por lo que no es necesario vincular a una biblioteca de importación. Sin embargo, debe tener una `typedef` instrucción `using` o que defina la firma de llamada de las funciones exportadas a las que llama.

- Llame a [FreeLibrary](freelibrary-and-afxfreelibrary.md) cuando haya terminado con el archivo dll.

Por ejemplo, esta función de ejemplo `LoadLibrary` llama a para cargar un archivo dll denominado "MyDLL `GetProcAddress` ", llama a para obtener un puntero a una función denominada "DLLFunc1", llama a la función y guarda el `FreeLibrary` resultado y, a continuación, llama a para descargar el archivo dll.

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

A diferencia de este ejemplo, en la mayoría de los `LoadLibrary` casos `FreeLibrary` se debe llamar a y solo una vez en la aplicación para un archivo dll determinado. Es especialmente cierto si va a llamar a varias funciones en el archivo DLL o llama a las funciones de DLL repetidamente.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Trabajar con bibliotecas de importación y archivos de exportación](reference/working-with-import-libraries-and-export-files.md)

- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
