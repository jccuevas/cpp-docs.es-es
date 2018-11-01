---
title: 'TN058: Implementación de estado del módulo MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.implementation
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: db34f528e70a7dcc437836684656b3ce8a4078fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626057"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: Implementación de estado del módulo MFC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota técnica describe la implementación de construcciones de "Estado del módulo" MFC. Una descripción de la implementación de estado de módulo es fundamental para usar la MFC compartidos de archivos DLL desde un archivo DLL (o de servidor OLE en proceso).

Antes de leer esta nota, consulte "Administrar el estado de datos de los módulos MFC" en [crear nuevos documentos, Windows y las vistas](../mfc/creating-new-documents-windows-and-views.md). En este artículo contiene información importante del uso y obtener información general sobre este tema.

## <a name="overview"></a>Información general

Hay tres tipos de información de estado MFC: estado del módulo, el estado de proceso y estado del subproceso. A veces se pueden combinar estos tipos de estado. Por ejemplo, asignaciones de identificadores de MFC son módulo local y local de subprocesos. Esto permite que dos módulos diferentes tener diferentes mapas en cada uno de sus subprocesos.

Estado de proceso y el estado de los subprocesos son similares. Estos elementos de datos son las cosas que han sido tradicionalmente las variables globales, pero que deba ser específico para un determinado proceso o subproceso para admite Win32s adecuado o compatibilidad con multithreading adecuado. Categoría a la que se ajusta un elemento de datos determinado depende de ese elemento y la semántica deseada con respecto a los límites del proceso y subproceso.

Estado del módulo es único en que puede contener realmente global estado o estado de proceso local o local de subprocesos. Además, se puede cambiar rápidamente.

## <a name="module-state-switching"></a>Cambio de estado del módulo

Cada subproceso contiene un puntero al estado de módulo "actual" o "active" (no es sorprendente que el puntero es parte del estado local de subproceso de MFC). Este puntero se cambia cuando el subproceso de ejecución supera un límite de módulo, como una aplicación a un Control OLE devolviendo la llamada a una aplicación o DLL o un Control OLE.

Se cambia el estado actual del módulo mediante una llamada a `AfxSetModuleState`. En su mayor parte, nunca se ocupará directamente con la API. MFC, en muchos casos, lo llamará automáticamente (en WinMain, puntos de entrada OLE, `AfxWndProc`, etcetera.). Esto se hace en cualquier componente que se escribe mediante vinculación estática en un especial `WndProc`y un especial `WinMain` (o `DllMain`) que sabe qué estado del módulo debe ser actual. Puede ver este código examinando DLLMODUL. CPP o APPMODUL. CPP en el directorio MFC\SRC.

Es raro que desea establecer el estado del módulo y, a continuación, no establecerlo de nuevo. La mayoría del tiempo que desee para su propio módulo "Insertar" de estado que el actual y, a continuación, cuando haya terminado, "el mensaje" el contexto original. Para ello, la macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) y la clase especial `AFX_MAINTAIN_STATE`.

`CCmdTarget` tiene características especiales para admitir el cambio de estado de módulo. En concreto, un `CCmdTarget` es la clase raíz que utiliza para la automatización OLE y COM OLE puntos de entrada. Al igual que cualquier otro punto de entrada se exponen en el sistema, estos puntos de entrada deben establecer el estado de módulo correcto. Cómo does un determinado `CCmdTarget` sabe lo que el estado del módulo "correcto" debe ser la respuesta es que "recuerda" ¿Qué es el estado del módulo "actual" cuando se construye, que se puede establecer el estado actual del módulo al que "recuerda" llamado valor cuando es una versión posterior. Como resultado, el módulo de estado que una determinada `CCmdTarget` objeto está asociado con es el estado del módulo que era el actual cuando se construye el objeto. Consideremos un ejemplo sencillo de un servidor en proceso de carga, la creación de un objeto y llamando a sus métodos.

1. Cargar la DLL OLE mediante `LoadLibrary`.

2. `RawDllMain` se llama primero. Establece el estado del módulo en el estado del módulo estático conocido para el archivo DLL. Por este motivo `RawDllMain` está vinculada estáticamente al archivo DLL.

1. Se llama al constructor para el generador de clases asociado con el objeto. `COleObjectFactory` se deriva de `CCmdTarget` y como resultado, recuerda en cada estado del módulo se creó una instancia. Esto es importante, cuando se solicita el generador de clases para crear objetos, ahora sabe qué estado de módulo para convertir en actual.

4. `DllGetClassObject` se llama para obtener el generador de clases. MFC busca en la lista de fábricas de clase asociada a este módulo y lo devuelve.

5. Se llama a `COleObjectFactory::XClassFactory2::CreateInstance`. Antes de crear el objeto y devolverlo, esta función establece el estado del módulo en el estado del módulo que era actual en el paso 3 (lo que era el actual cuando el `COleObjectFactory` se creó una instancia). Esto se realiza dentro de [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Cuando se crea el objeto, también es un `CCmdTarget` derivados y de la misma manera `COleObjectFactory` recuerdan el estado del módulo estuvo activo, también lo hace este nuevo objeto. Ahora el objeto sabe qué estado de módulo para cambiar a cada vez que se llama.

1. El cliente llama a una función en el objeto OLE COM que recibió de su `CoCreateInstance` llamar. Cuando se llama al objeto utiliza `METHOD_PROLOGUE` para cambiar el estado del módulo igual que `COleObjectFactory` does.

Como puede ver, el estado del módulo se propaga desde el objeto al objeto cuando se crean. Es importante que establezca correctamente el estado del módulo. Si no se establece, el archivo DLL o un objeto COM puede interactuar mal con una aplicación MFC que llama, o puede ser no se puede encontrar sus propios recursos o puede producir un error de otras maneras lamentable.

Tenga en cuenta que ciertos tipos de archivos DLL, específicamente "Extensión de MFC" DLL no cambie el estado del módulo en sus `RawDllMain` (en realidad, normalmente ni siquiera es necesario un `RawDllMain`). Esto es porque se han diseñado para comportarse "como si" fueran realmente presentes en la aplicación que los usa. Son una parte muy relevante de la aplicación que se está ejecutando y es su intención de modificar el estado global de la aplicación.

Controles OLE y otros archivos DLL es muy diferente. ¿Desea modificar el estado de la aplicación que realiza la llamada; la aplicación que llama a ellos no puede ser incluso una aplicación MFC y lo que no puede haber ningún estado para modificar. Este es el motivo que se inventó el cambio de estado de módulo.

Para las funciones exportadas desde un archivo DLL, como el que se abre un cuadro de diálogo en el archivo DLL, deberá agregar el código siguiente al principio de la función:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Esto cambia el estado actual del módulo con el estado devuelto desde [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) hasta el final del ámbito actual.

Si no se usa la macro AFX_MODULE_STATE, se producirán problemas con los recursos en archivos DLL. De forma predeterminada, MFC utiliza el identificador de recurso de la aplicación principal para cargar la plantilla de recursos. Esta plantilla se almacena realmente en el archivo DLL. La causa es que no ha cambiado la información de estado del módulo de MFC mediante la macro AFX_MODULE_STATE. El identificador de recurso se recuperó de estado del módulo de MFC. Si no se cambia el estado del módulo hace que el identificador de recurso incorrecto que se usará.

AFX_MODULE_STATE no debe colocarse en todas las funciones en el archivo DLL. Por ejemplo, `InitInstance` pueden llamarse mediante el código de MFC en la aplicación sin AFX_MODULE_STATE porque MFC cambia automáticamente el estado del módulo antes de `InitInstance` y, a continuación, vuelve a cambiar el lo después `InitInstance` devuelve. Lo mismo puede decirse de todos los controladores de mapa de mensajes. Archivos DLL de MFC estándar tiene realmente un procedimiento de ventana maestro que cambia automáticamente el estado del módulo antes de enrutar cualquier mensaje.

## <a name="process-local-data"></a>Procesamiento de datos Local

Procesamiento de datos local no sería tales bastante problemático no hubiera la dificultad del modelo Win32s DLL. En Win32s todos los archivos DLL comparten sus datos globales, incluso cuando la carga entre varias aplicaciones. Esto es muy diferente desde el modelo de datos de archivo DLL para Win32 "real", donde cada DLL Obtiene una copia independiente de su espacio de datos en todos los procesos que se adjunta al archivo DLL. Para agregar a la complejidad, los datos asignados en el montón en un archivo DLL de Win32s están en realidad proceso específico (al menos en cuanto sale de la propiedad). Tenga en cuenta los datos y el código siguiente:

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

Imagine qué ocurre si el código anterior está en ubicado en un archivo DLL y que se carga la DLL mediante dos procesos A y B (de hecho, podría ser dos instancias de la misma aplicación). Una de las llamadas `SetGlobalString("Hello from A")`. Como resultado, se asigna memoria para el `CString` datos en el contexto del proceso de r. tenga en cuenta que el `CString` propio es global y es visible para tanto A y B. Ahora llama B `GetGlobalString(sz, sizeof(sz))`. B será capaz de ver los datos de conjunto. Esto es porque Win32s no ofrece ninguna protección entre procesos, como Win32. Es el primer problema; en muchos casos no es recomendable tener una aplicación que afectan a los datos globales que se consideran que la propiedad de una aplicación diferente.

Hay también otros problemas. Supongamos que ahora se cierra. Cuando se cierra un, la memoria utilizada por la '`strGlobal`' cadena está disponible para el sistema, es decir, se libera automáticamente toda la memoria asignada por un proceso por el sistema operativo. No se libera porque el `CString` se llama al destructor; todavía no se ha llamado todavía. Que se libere simplemente porque la aplicación que lo asignó ha dejado la escena. Ahora, si llama B `GetGlobalString(sz, sizeof(sz))`, no se puede obtener datos válidos. Puede que otra aplicación ha usado esa memoria para otra cosa.

Claramente que exista un problema. MFC 3.x utiliza una técnica denominada almacenamiento local de subprocesos (TLS). MFC 3.x asignaría un índice TLS que bajo Win32s realmente actúa como un índice de almacenamiento local de proceso, incluso si no que se llama y, a continuación, podría hacer referencia a todos los datos basándose en ese índice TLS. Esto es similar al índice TLS que se usó para almacenar datos locales del subproceso de Win32 (vea a continuación para obtener más información sobre ese tema). Esto debe utilizar al menos dos índices TLS por proceso cada DLL de MFC. Cuando la cuenta para cargar muchas OLE Control dll (OCX), rápidamente ejecutar fuera de los índices TLS (hay solo 64 disponibles). Además, MFC tuvo que realizar todos estos datos en un solo lugar, en una única estructura. No fue muy extensible y no era ideal con respecto a su uso de índices TLS.

MFC 4.x soluciona este problema con un conjunto de plantillas de clase puede "ajuste" alrededor de los datos que deben ser el proceso local. Por ejemplo, se podría solucionar el problema mencionado anteriormente escribiendo:

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

MFC implementa esto en dos pasos. En primer lugar, hay un nivel por encima de Win32 __Tls\*__  API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, etc.) que usar solo dos índices TLS por proceso, independientemente de cuántos archivos DLL que tiene. Segundo, el `CProcessLocal` se proporciona una plantilla para tener acceso a estos datos. Invalida el operador -> que es lo que permite la sintaxis intuitiva que vea más arriba. Todos los objetos que están encapsulados por `CProcessLocal` debe derivarse de `CNoTrackObject`. `CNoTrackObject` Proporciona un asignador de nivel inferior (**LocalAlloc**/**LocalFree**) y un destructor virtual que MFC puede destruir automáticamente los objetos de proceso local cuando se finaliza el proceso. Estos objetos pueden tener un destructor personalizado si es necesaria realizar una limpieza adicional. El ejemplo anterior no requiere uno, puesto que el compilador generará un destructor predeterminado para destruir el objeto incrustado `CString` objeto.

Hay otras ventajas de este enfoque interesantes. No sólo son todas `CProcessLocal` objetos que se destruyen automáticamente, no se construyen hasta que se necesitan. `CProcessLocal::operator->` creará una instancia del objeto asociado de la primera vez que se llama y no antes. En el ejemplo anterior, eso significa que la '`strGlobal`' no se construirá la cadena hasta la primera vez `SetGlobalString` o `GetGlobalString` se llama. En algunos casos, esto puede ayudar a reducir el tiempo de inicio DLL.

## <a name="thread-local-data"></a>Datos locales de subproceso

Similar a procesar los datos locales, los datos locales de subproceso se usan cuando los datos deben ser locales en un subproceso determinado. Es decir, se necesita una instancia independiente de los datos para cada subproceso que tiene acceso a esos datos. Esto muchas veces se puede usar en lugar de mecanismos de sincronización extenso. Si los datos no se necesitan ser compartidos por varios subprocesos, estos mecanismos pueden ser costosa e innecesaria. Supongamos que tenemos un `CString` objeto (muy similar a la del ejemplo anterior). Podemos hacerla de subproceso local incluyéndolo con un `CThreadLocal` plantilla:

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

Si `MakeRandomString` se llamó desde dos subprocesos diferentes, cada uno de ellos sería "aleatorio" la cadena de maneras diferentes sin interferir con las demás. Esto es porque no hay realmente una `strThread` instancia por subproceso, en lugar de una sola instancia global.

Tenga en cuenta cómo se utiliza una referencia para capturar el `CString` de direcciones una vez en lugar de una vez por cada iteración del bucle. El código del bucle for podría haberse escrito con `threadData->strThread` everywhere '`str`' se usa, pero el código sería mucho más lento en ejecución. Es mejor almacenar en caché una referencia a los datos cuando se producen dichas referencias en bucles.

El `CThreadLocal` plantilla de clase utiliza los mismos mecanismos que `CProcessLocal` no y las mismas técnicas de implementación.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
