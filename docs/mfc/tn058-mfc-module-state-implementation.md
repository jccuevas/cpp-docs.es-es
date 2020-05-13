---
title: 'TN058: Implementación de estado del módulo MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: b64fb6b97474007c44a2124315e83e1ac119f9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366607"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: Implementación de estado del módulo MFC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota técnica describe la implementación de construcciones de "estado de módulo" de MFC. Una comprensión de la implementación de estado del módulo es fundamental para usar los archivos DLL compartidos de MFC desde un archivo DLL (o un servidor OLE en proceso).

Antes de leer esta nota, consulte "Administración de los datos de estado de los módulos MFC" en Creación de [nuevos documentos, Ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md). Este artículo contiene información de uso importante e información general sobre este tema.

## <a name="overview"></a>Información general

Hay tres tipos de información de estado MFC: estado de módulo, estado de proceso y estado de subproceso. A veces, estos tipos de estado se pueden combinar. Por ejemplo, las asignaciones de identificador de MFC son locales de módulo y locales de subprocesos. Esto permite que dos módulos diferentes tengan mapas diferentes en cada uno de sus subprocesos.

El estado del proceso y el estado del subproceso son similares. Estos elementos de datos son cosas que tradicionalmente han sido variables globales, pero tienen que ser específicos de un proceso o subproceso determinado para la compatibilidad adecuada con Win32s o para la compatibilidad adecuada con multithreading. La categoría en la que cabe un elemento de datos determinado depende de ese elemento y de su semántica deseada con respecto a los límites de proceso y subproceso.

El estado del módulo es único en el que puede contener un estado o estado verdaderamente global que sea local de proceso o local de subprocesos. Además, se puede cambiar rápidamente.

## <a name="module-state-switching"></a>Cambio de estado del módulo

Cada subproceso contiene un puntero al estado del módulo "actual" o "activo" (no es de extrañar que el puntero forme parte del estado local del subproceso de MFC). Este puntero se cambia cuando el subproceso de ejecución pasa un límite de módulo, como una aplicación que llama a un control OLE o DLL, o un control OLE que vuelve a llamar a una aplicación.

El estado actual del módulo `AfxSetModuleState`se cambia llamando a . En su mayor parte, nunca tratará directamente con la API. MFC, en muchos casos, lo llamará por usted (en `AfxWndProc`WinMain, puntos de entrada OLE, , etc.). Esto se hace en cualquier componente que escriba `WndProc`vinculando estáticamente en un especial, y un especial `WinMain` (o `DllMain`) que sepa qué estado del módulo debe ser actual. Puede ver este código mirando DLLMODUL. CPP o APPMODUL. CPP en el directorio MFC-SRC.

Es raro que desee establecer el estado del módulo y, a continuación, no volver a establecerlo. La mayoría de las veces desea "empujar" su propio estado de módulo como el actual y luego, después de que haya terminado, "pop" el contexto original de nuevo. Esto lo hace el [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) macro `AFX_MAINTAIN_STATE`y la clase especial .

`CCmdTarget`tiene características especiales para soportar la conmutación de estado del módulo. En particular, `CCmdTarget` a es la clase raíz utilizada para la automatización OLE y los puntos de entrada OLE COM. Al igual que cualquier otro punto de entrada expuesto al sistema, estos puntos de entrada deben establecer el estado correcto del módulo. ¿Cómo un `CCmdTarget` determinado sabe cuál debe ser el estado del módulo "correcto" La respuesta es que "recuerda" cuál es el estado del módulo "actual" cuando se construye, de modo que puede establecer el estado del módulo actual en ese valor "recordado" cuando se llama más tarde. Como resultado, el estado del `CCmdTarget` módulo al que está asociado un objeto determinado es el estado del módulo que era actual cuando se construyó el objeto. Tome un ejemplo sencillo de cargar un servidor INPROC, crear un objeto y llamar a sus métodos.

1. OLE carga el archivo `LoadLibrary`DLL mediante .

1. `RawDllMain`se llama primero. Establece el estado del módulo en el estado de módulo estático conocido para el archivo DLL. Por esta `RawDllMain` razón está vinculado estáticamente a la DLL.

1. Se llama al constructor del generador de clases asociado a nuestro objeto. `COleObjectFactory`se deriva `CCmdTarget` de y como resultado, recuerda en qué estado de módulo se crea una instancia. Esto es importante: cuando se pide al generador de clases que cree objetos, ahora sabe qué estado de módulo se va a hacer actual.

1. `DllGetClassObject`está llamado a obtener la fábrica de clases. MFC busca la lista de generador de clases asociada a este módulo y la devuelve.

1. Se llama a `COleObjectFactory::XClassFactory2::CreateInstance`. Antes de crear el objeto y devolverlo, esta función establece el estado del módulo en `COleObjectFactory` el estado del módulo que estaba actual en el paso 3 (el que estaba actualizado cuando se creó una instancia de la instancia). Esto se hace dentro de [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Cuando se crea el objeto, `CCmdTarget` también es una `COleObjectFactory` derivada y de la misma manera se recuerda qué estado de módulo estaba activo, también lo hace este nuevo objeto. Ahora el objeto sabe a qué estado de módulo cambiar cada vez que se llama.

1. El cliente llama a una función en `CoCreateInstance` el objeto OLE COM que recibió de su llamada. Cuando se llama al `METHOD_PROLOGUE` objeto se utiliza `COleObjectFactory` para cambiar el estado del módulo al igual que lo hace.

Como puede ver, el estado del módulo se propaga de objeto a objeto a medida que se crean. Es importante que el estado del módulo se establezca correctamente. Si no se establece, el objeto DLL o COM puede interactuar mal con una aplicación MFC que lo está llamando, o puede no ser capaz de encontrar sus propios recursos, o puede producir un error de otras maneras miserables.

Tenga en cuenta que ciertos tipos de archivos DLL, específicamente los archivos `RawDllMain` DLL de "extensión MFC" `RawDllMain`no cambian el estado del módulo en su (en realidad, por lo general ni siquiera tienen un ). Esto se debe a que están destinados a comportarse "como si" estuvieran realmente presentes en la aplicación que los utiliza. Son una parte de la aplicación que se está ejecutando y es su intención modificar el estado global de esa aplicación.

Los controles OLE y otros archivos DLL son muy diferentes. No quieren modificar el estado de la aplicación que realiza la llamada; la aplicación que les está llamando puede que ni siquiera sea una aplicación MFC, por lo que puede no haber ningún estado para modificar. Esta es la razón por la que se inventó la conmutación de estado del módulo.

Para las funciones exportadas desde un archivo DLL, como una que inicia un cuadro de diálogo en el archivo DLL, debe agregar el código siguiente al principio de la función:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Esto intercambia el estado del módulo actual con el estado devuelto desde [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) hasta el final del ámbito actual.

Se producirán problemas con los recursos de los archivos DLL si no se utiliza la macro AFX_MODULE_STATE. De forma predeterminada, MFC usa el identificador de recursos de la aplicación principal para cargar la plantilla de recursos. Esta plantilla se almacena realmente en el archivo DLL. La causa raíz es que la macro de AFX_MODULE_STATE no ha cambiado la información de estado del módulo de MFC. El identificador de recursos se recupera del estado del módulo de MFC. Si no se cambia el estado del módulo, se utiliza el identificador de recursos incorrecto.

AFX_MODULE_STATE no es necesario poner en todas las funciones del archivo DLL. Por ejemplo, `InitInstance` el código MFC de la aplicación puede llamarlo a `InitInstance` él sin AFX_MODULE_STATE `InitInstance` porque MFC cambia automáticamente el estado del módulo antes y, a continuación, lo vuelve a cambiar después de las devoluciones. Lo mismo es cierto para todos los controladores de mapa de mensajes. Los archivos DLL de MFC normales tienen realmente un procedimiento de ventana maestra especial que cambia automáticamente el estado del módulo antes de enrutar cualquier mensaje.

## <a name="process-local-data"></a>Procesar datos locales

Procesar datos locales no sería de gran preocupación si no hubiera sido por la dificultad del modelo DLL Win32s. En Win32s, todos los archivos DLL comparten sus datos globales, incluso cuando se cargan en varias aplicaciones. Esto es muy diferente del modelo de datos DLL de Win32 "real", donde cada DLL obtiene una copia independiente de su espacio de datos en cada proceso que se adjunta al archivo DLL. Para agregar a la complejidad, los datos asignados en el montón en un archivo DLL de Win32s son de hecho específicos del proceso (al menos en lo que respecta a la propiedad). Tenga en cuenta los siguientes datos y código:

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

Considere lo que sucede si el código anterior está ubicado en un archivo DLL y ese archivo DLL se carga mediante dos procesos A y B (de hecho, podría ser dos instancias de la misma aplicación). Una `SetGlobalString("Hello from A")`llamada . Como resultado, la memoria `CString` se asigna para los datos en el `CString` contexto del proceso A. Tenga en cuenta que el sí mismo es global y es visible para A y B. Ahora B `GetGlobalString(sz, sizeof(sz))`llama . B podrá ver los datos que A establece. Esto se debe a que Win32s no ofrece protección entre procesos como Win32. Ese es el primer problema; en muchos casos no es deseable que una aplicación afecte a los datos globales que se considera propiedad de una aplicación diferente.

Hay problemas adicionales también. Digamos que la A ahora sale. Cuando A sale, la memoria`strGlobal`utilizada por la cadena ' ' está disponible para el sistema, es decir, toda la memoria asignada por el proceso A se libera automáticamente por el sistema operativo. No se libera porque `CString` se llama al destructor; aún no se ha llamado. Se libera simplemente porque la aplicación que lo asignó ha salido de la escena. Ahora, si `GetGlobalString(sz, sizeof(sz))`B llamó , puede que no obtenga datos válidos. Alguna otra aplicación puede haber utilizado esa memoria para otra cosa.

Claramente existe un problema. MFC 3.x utiliza una técnica denominada almacenamiento local de subprocesos (TLS). MFC 3.x asignaría un índice TLS que en Win32s realmente actúa como un índice de almacenamiento local de proceso, aunque no se llama a eso y, a continuación, haría referencia a todos los datos basados en ese índice TLS. Esto es similar al índice TLS que se usó para almacenar datos locales de subprocesos en Win32 (consulte a continuación para obtener más información sobre ese tema). Esto provocó que cada DLL de MFC utilizara al menos dos índices TLS por proceso. Cuando se contabiliza para cargar muchos archivos DLL de control OLE (OXP), se agota rápidamente los índices TLS (solo hay 64 disponibles). Además, MFC tenía que colocar todos estos datos en un solo lugar, en una sola estructura. No era muy extensible y no era ideal con respecto a su uso de índices TLS.

MFC 4.x soluciona esto con un conjunto de plantillas de clase que puede "envolver" alrededor de los datos que deben ser locales de proceso. Por ejemplo, el problema mencionado anteriormente podría solucionarse escribiendo:

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC implementa esto en dos pasos. En primer lugar, hay una capa encima de las API __de\* Tls__ de Win32 (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, etc.) que utilizan solo dos índices TLS por proceso, independientemente de cuántos archivos DLL tenga. En segundo `CProcessLocal` lugar, se proporciona la plantilla para acceder a estos datos. Anula la > operador, que es lo que permite la sintaxis intuitiva que se ve arriba. Todos los objetos `CProcessLocal` que se ajustan `CNoTrackObject`por deben derivarse de . `CNoTrackObject`proporciona un asignador de nivel inferior (**LocalAlloc**/**LocalFree**) y un destructor virtual de modo que MFC puede destruir automáticamente los objetos locales del proceso cuando finaliza el proceso. Estos objetos pueden tener un destructor personalizado si se requiere una limpieza adicional. El ejemplo anterior no requiere uno, ya que el compilador `CString` generará un destructor predeterminado para destruir el objeto incrustado.

Hay otras ventajas interesantes para este enfoque. No sólo `CProcessLocal` todos los objetos se destruyen automáticamente, no se construyen hasta que se necesitan. `CProcessLocal::operator->`creará una instancia del objeto asociado la primera vez que se llama, y no antes. En el ejemplo anterior, eso`strGlobal`significa que la cadena ' `SetGlobalString` ' `GetGlobalString` no se construirá hasta la primera vez o se llama. En algunos casos, esto puede ayudar a reducir el tiempo de inicio de DLL.

## <a name="thread-local-data"></a>Datos locales de subprocesos

De forma similar al procesamiento de datos locales, los datos locales de subprocesos se usan cuando los datos deben ser locales para un subproceso determinado. Es decir, necesita una instancia independiente de los datos para cada subproceso que tiene acceso a esos datos. Esto se puede utilizar muchas veces en lugar de mecanismos de sincronización extensos. Si no es necesario compartir los datos por varios subprocesos, estos mecanismos pueden ser costosos e innecesarios. Supongamos que `CString` teníamos un objeto (muy parecido a la muestra anterior). Podemos hacerlo enhebrado local `CThreadLocal` envolviéndolo con una plantilla:

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

Si `MakeRandomString` se llama desde dos subprocesos diferentes, cada uno "barajaría" la cadena de diferentes maneras sin interferir con el otro. Esto se debe a `strThread` que en realidad hay una instancia por subproceso en lugar de una sola instancia global.

Observe cómo se utiliza una `CString` referencia para capturar la dirección una vez en lugar de una vez por iteración de bucle. El código de bucle `threadData->strThread` podría haber`str`sido escrito con todas partes ' ' se utiliza, pero el código sería mucho más lento en la ejecución. Es mejor almacenar en caché una referencia a los datos cuando estas referencias se producen en bucles.

La `CThreadLocal` plantilla de clase utiliza `CProcessLocal` los mismos mecanismos que y las mismas técnicas de implementación.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
