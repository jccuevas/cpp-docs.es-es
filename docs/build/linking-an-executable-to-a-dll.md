---
title: Vincular un ejecutable a un archivo DLL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e72cc680036d2c7e3737e5512c73115e29562018
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692220"
---
# <a name="link-an-executable-to-a-dll"></a>Vincular un ejecutable a un archivo DLL  
  
Un archivo ejecutable se vincula a (o carga) un archivo DLL de dos maneras:  
  
-   *Vinculación implícita*, donde se carga el archivo DLL en el sistema operativo cuando se carga el archivo ejecutable desde él. El archivo ejecutable cliente llama a las funciones exportadas del archivo DLL como si las funciones estaban vinculadas estáticamente y contenidas dentro del archivo ejecutable. Vinculación implícita se denomina a veces *carga estática* o *vinculación dinámica en tiempo de carga*.  
  
-   *Vinculación explícita*, donde el sistema operativo carga la DLL a petición en tiempo de ejecución. Un archivo ejecutable que utiliza un archivo DLL mediante la vinculación explícita debe realizar llamadas de función para cargar y descargar el archivo DLL explícitamente y tener acceso a las funciones exportadas por el archivo DLL. A diferencia de las llamadas a funciones en una biblioteca vinculada estáticamente, el archivo ejecutable cliente debe llamar a las funciones exportadas en un archivo DLL mediante un puntero a función. Vinculación explícita se denomina a veces *carga dinámica* o *vinculación dinámica en tiempo de ejecución*.  
  
Un archivo ejecutable puede usar cualquier método de vinculación para vincular a la misma DLL. Además, estos métodos no son mutuamente excluyentes; un archivo ejecutable puede vincularse implícitamente a un archivo DLL y otro puede asociarse a ella explícitamente.  
  
<a name="determining-which-linking-method-to-use"></a>  
  
## <a name="determine-which-linking-method-to-use"></a>Determinar el método de vinculación que se debe utilizar  
  
Si se debe utilizar la vinculación implícita o vinculación explícita es una decisión de arquitectura que debe realizar para la aplicación. Existen ventajas y desventajas en cada método.  
  
### <a name="implicit-linking"></a>Vinculación implícita  
  
Vinculación implícita se produce cuando el código de la aplicación llama a una función exportada del archivo DLL. Cuando se compila o ensambla el código fuente para el archivo ejecutable de llamada, la llamada a la función del archivo DLL genera una referencia de función externa en el código objeto. Para resolver esta referencia externa, la aplicación debe vincularse a la biblioteca de importación (archivo .LIB) proporcionada por el autor del archivo DLL.  
  
La biblioteca de importación sólo contiene código para cargar el archivo DLL e implementar llamadas a las funciones del archivo DLL. Cuando se encuentra una función externa en una biblioteca de importación, se notifica al vinculador que el código de la función está en un archivo DLL. Para resolver referencias externas a archivos DLL, el vinculador simplemente agregará información al archivo ejecutable para indicar al sistema dónde se encuentra el código del archivo DLL cuando se inicie el proceso.  
  
Cuando el sistema inicia un programa que contiene referencias vinculadas dinámicamente, utiliza esta información en el archivo ejecutable del programa para encontrar los archivos DLL necesarios. Si no encuentra el archivo DLL, el sistema finalizará el proceso y mostrará un cuadro de diálogo para notificar el error. En caso contrario, el sistema asigna los módulos de DLL al espacio de direcciones del proceso.  
  
Si cualquiera de los archivos DLL tiene una función de punto de entrada para el código de inicialización y finalización como `DllMain`, el sistema operativo llama a la función. Uno de los parámetros pasados a la función de punto de entrada especifica un código que indica que se está asociando el archivo DLL al proceso. Si la función de punto de entrada no devuelve el valor TRUE, el sistema finalizará el proceso y notificará un error.  
  
Por último, el sistema modifica el código ejecutable del proceso para proporcionar direcciones de inicio a las funciones del archivo DLL.  
  
Como el resto del código de un programa, el código de un archivo DLL se asigna al espacio de direcciones del proceso cuando éste se inicie y sólo se carga en memoria cuando sea necesario. Como resultado, el `PRELOAD` y `LOADONCALL` los atributos de código que utiliza archivos .def para controlar la carga en las versiones anteriores de Windows ya no tienen un significado.  
  
### <a name="explicit-linking"></a>Vinculación explícita  
  
La mayoría de las aplicaciones utilizan la vinculación implícita, puesto que es el método de vinculación más sencillo de utilizar. Sin embargo, hay veces cuando la vinculación explícita es necesaria. Algunas de las razones más frecuentes para utilizar la vinculación explícita son:  
  
-   La aplicación no conoce el nombre de un archivo DLL que se carga hasta el tiempo de ejecución. Por ejemplo, la aplicación puede obtener el nombre del archivo DLL y las funciones exportadas desde un archivo de configuración en el inicio.  
  
-   Si no se encuentra el archivo DLL al iniciarse el proceso, se termina un proceso que utilice vinculación implícita por el sistema operativo. Un proceso que utilice vinculación explícita no finaliza en esta situación y puede intentar recuperarse del error. Por ejemplo, podría notificar el error al usuario y pedirle que especifique otra ruta de acceso al archivo DLL.  
  
-   Un proceso que utilice vinculación implícita también finaliza si cualquiera de los archivos DLL esté vinculado incluye una `DllMain` función que se produce un error. Un proceso que utilice vinculación explícita no finaliza en esta situación.  
  
-   Una aplicación que se vincule implícitamente a muchos archivos DLL puede resultar lenta de inicializar, puesto que Windows cargará todos los archivos DLL cuando se cargue la aplicación. Para mejorar el rendimiento de inicio, una aplicación puede vincularse implícitamente únicamente a esos archivos DLL necesarios inmediatamente después de la carga y esperar hasta que otros archivos DLL necesarios para vincular explícitamente a ellos.  
  
-   Vinculación explícita elimina la necesidad de vincular la aplicación mediante el uso de una biblioteca de importación. Si los cambios en el archivo DLL hacen que cambien los ordinales de exportación, las aplicaciones que usan la vinculación explícita no es necesario volver a vincular si llaman a `GetProcAddress` con el nombre de una función y no es un valor ordinal, mientras que las aplicaciones que utilizan la vinculación implícita deberán volver a vincularse a la nueva biblioteca de importación.  
  
Hay que tener en cuenta dos posibles peligros en la vinculación explícita:  
  
-   Si el archivo DLL tiene una `DllMain` función de punto de entrada, el sistema operativo llama a la función en el contexto del subproceso que llama `LoadLibrary`. No se llama a la función de punto de entrada si el archivo DLL ya está asociado al proceso a causa de una llamada anterior a `LoadLibrary` que ha tenido una llamada correspondiente a la `FreeLibrary` función. Vinculación explícita puede producir problemas si el archivo DLL utiliza un `DllMain` función para realizar la inicialización de cada subproceso de un proceso dado que ya existen subprocesos cuando `LoadLibrary` (o `AfxLoadLibrary`) se llama no se inicializan.  
  
-   Si un archivo DLL declara datos de extensión estática como `__declspec(thread)`, que puede causar un error de protección si se vincula explícitamente. Una vez cargado el archivo DLL mediante una llamada a `LoadLibrary`, se producirá un error de protección siempre que el código hace referencia a estos datos. Entre los datos de extensión estática se incluyen elementos estáticos globales y locales. Por lo tanto, cuando se crea un archivo DLL, debe evitar el uso de almacenamiento local de subprocesos o informar a los usuarios del archivo DLL acerca de los problemas potenciales de cargar dinámicamente el archivo DLL. Para obtener más información, consulte [mediante almacenamiento local de subprocesos en una biblioteca de vínculos dinámicos (Windows SDK)](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library).  
  
<a name="linking-implicitly"></a>  
  
## <a name="how-to-link-implicitly-to-a-dll"></a>Cómo vincular implícitamente a un archivo DLL  
  
Para usar un archivo DLL mediante la vinculación implícita, los ejecutables de cliente deben obtener estos archivos desde el proveedor del archivo DLL:  
  
-   Uno o varios archivos de encabezado (.h archivos) que contienen las declaraciones de los datos exportados, funciones o clases de C++ en el archivo DLL. Las clases, funciones y los datos exportados por el archivo DLL deben estar marcados `__declspec(dllimport)` en el archivo de encabezado. Para obtener más información, consulte [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
-   Una biblioteca de importación para vincular en el archivo ejecutable. El vinculador crea la biblioteca de importación cuando se compila el archivo DLL. Para obtener más información, consulte [. Los archivos LIB](../build/reference/dot-lib-files-as-linker-input.md).  
  
-   El archivo DLL real.  
  
Para usar un archivo DLL mediante la vinculación implícita, un archivo ejecutable debe incluir los archivos de encabezado que declaran los datos, funciones o clases de C++ exportadas por el archivo DLL en cada archivo de código fuente que contiene las llamadas a los datos exportados, funciones y clases. Desde una perspectiva de programación, las llamadas a las funciones exportadas son como cualquier otra llamada de función.  
  
Para compilar el archivo ejecutable de llamada deberá vincularlo a la biblioteca de importación. Si usa un archivo MAKE externo o sistema de compilación, especifique el nombre de archivo de la biblioteca de importación donde se indican otros archivos objeto (.obj) o bibliotecas que se vinculan.  
  
El sistema operativo deberá ser capaz de encontrar el archivo DLL cuando cargue el archivo ejecutable de llamada. Esto significa que la aplicación debe implementar o comprobar la existencia del archivo DLL cuando se instala la aplicación.   
  
<a name="linking-explicitly"></a>  
  
## <a name="how-to-link-explicitly-to-a-dll"></a>Cómo crear un vínculo explícito a un archivo DLL  
  
Para usar un archivo DLL mediante la vinculación explícita, las aplicaciones deben llamar a una función para cargar explícitamente el archivo DLL en tiempo de ejecución. Para una vinculación explícita a un archivo DLL, una aplicación debe:  
  
-   Llame a [LoadLibrary](loadlibrary-and-afxloadlibrary.md), `LoadLibraryEx`, o una función similar para cargar el archivo DLL y obtener un identificador de módulo.  
  
-   Llame a [GetProcAddress](getprocaddress.md) obtener un puntero de función a cada función exportada que llama la aplicación. Dado que las aplicaciones llaman a las funciones DLL mediante un puntero, el compilador no genera referencias externas, por lo que no es necesario para vincular con una biblioteca de importación. Sin embargo, debe tener un `typedef` o `using` instrucción que define la signatura de llamada de las funciones exportadas que llamar.   
  
-   Llame a [FreeLibrary](freelibrary-and-afxfreelibrary.md) cuando haya terminado con el archivo DLL.  
  
Por ejemplo, llama esta función de ejemplo `LoadLibrary` cargar un archivo DLL denominado "MyDLL", las llamadas a `GetProcAddress` para obtener un puntero a una función denominada "DLLFunc1", llama a la función y guarda el resultado y, a continuación, llama a `FreeLibrary` para descargar el archivo DLL. 
  
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
  
A diferencia de en este ejemplo, en la mayoría de los casos debe llamar a `LoadLibrary` y `FreeLibrary` solo una vez en la aplicación para una DLL determinada, especialmente si va a llamar a varias funciones en el archivo DLL o llamar a DLL funciones varias veces.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Trabajar con bibliotecas de importación y archivos de exportación](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/desktop/Dlls/dynamic-link-library-search-order)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)