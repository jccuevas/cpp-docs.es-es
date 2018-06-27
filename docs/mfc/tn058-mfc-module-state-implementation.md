---
title: 'TN058: Implementación de estado del módulo MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.implementation
dev_langs:
- C++
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9702e57cb893c4018662a9bd1713342ba199d06d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952845"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: Implementación de estado del módulo MFC
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota técnica describe la implementación de construcciones de "Estado del módulo" MFC. Una descripción de la implementación de estado de módulo es fundamental para usar la MFC compartidos de archivos DLL desde un archivo DLL (o servidor OLE en proceso).  
  
 Antes de leer esta nota, consulte "Administrar el estado de datos de los módulos MFC" en [crear nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md). Este artículo contiene información importante del uso y obtener información general sobre este tema.  
  
## <a name="overview"></a>Información general  
 Hay tres tipos de información de estado MFC: estado del módulo, el estado del proceso y el estado de subproceso. A veces se pueden combinar estos tipos de estado. Por ejemplo, las asignaciones de identificadores de MFC son módulo local y local de subprocesos. Esto permite que dos módulos diferentes tener asignaciones diferentes en cada uno de los subprocesos.  
  
 Estado del proceso y el estado de los subprocesos son similares. Estos elementos de datos son cosas que han sido tradicionalmente variables globales, pero que deba ser específico para un determinado proceso o subproceso para admite Win32s apropiado o para la compatibilidad con subprocesamiento múltiple apropiado. Categoría a la que se ajusta un elemento de datos determinado depende de ese elemento y su semántica deseada con respecto a los límites de procesos y subprocesos.  
  
 Estado del módulo es único en que puede contener realmente global estado o estado de proceso local o local de subprocesos. Además, se puede cambiar rápidamente.  
  
## <a name="module-state-switching"></a>Cambio de estado del módulo  
 Cada subproceso contiene un puntero al estado de módulo "activos" o "actual" (evidentemente, el puntero es parte de estado local de subproceso de MFC). This (puntero) se cambia cuando el subproceso de ejecución supera un límite de módulo, por ejemplo, una aplicación que llama en un Control OLE o archivo DLL o un Control OLE llamadas a una aplicación.  
  
 Se cambia el estado actual del módulo mediante una llamada a `AfxSetModuleState`. En general, nunca abordará directamente con la API. MFC, en muchos casos, lo llamará automáticamente (en WinMain, puntos de entrada OLE, `AfxWndProc`, etcetera.). Esto se hace en cualquier componente escrito mediante la vinculación estática en una clase especial `WndProc`y una clase especial `WinMain` (o `DllMain`) que sabe qué estado del módulo debe estar actualizada. Puede ver este código examinando DLLMODUL. CPP o APPMODUL. CPP en el directorio MFC\SRC.  
  
 Es raro que desea establecer el estado del módulo y, a continuación, no vuelve a establecerlo. La mayoría del tiempo que desea "push" su propio módulo de estado como el actual y, a continuación, una vez haya terminado, "pop" volver el contexto original. Para ello, la macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) y la clase especial `AFX_MAINTAIN_STATE`.  
  
 `CCmdTarget` tiene características especiales para admitir el cambio de estado de módulo. En concreto, un `CCmdTarget` es la clase raíz que usa para la automatización OLE y OLE y COM puntos de entrada. Al igual que cualquier otro punto de entrada expuestos en el sistema, estos puntos de entrada deben establecer el estado de módulo correcto. Cómo does un determinado `CCmdTarget` sabe lo que el estado del módulo "correcto" debe ser la respuesta es que "recuerda" ¿Qué es el estado del módulo "actual" cuando se construye, por ejemplo, que se puede establecer el estado actual del módulo al que "recuerda" denominado valor cuando es posterior. Como resultado, el módulo de estado que un determinado `CCmdTarget` objeto se asocia con es el estado del módulo que estaba activo cuando se creó el objeto. Consideremos un ejemplo sencillo de un servidor en proceso de carga, creación de un objeto y llamando a sus métodos.  
  
1.  Cargar la DLL OLE mediante `LoadLibrary`.  
  
2. `RawDllMain` se llama en primer lugar. Establece el estado del módulo en el estado del módulo estático conocido para el archivo DLL. Por esta razón `RawDllMain` está vinculada estáticamente a la DLL.  
  
3.  Se llama al constructor para el generador de clases asociado con nuestro objeto. `COleObjectFactory` se deriva de `CCmdTarget` y como resultado, recuerda en qué estado del módulo que se crean las instancias. Esto es importante: cuando se solicita el generador de clases para crear objetos, ahora sabe qué estado del módulo para convertir en actual.  
  
4. `DllGetClassObject` se llama para obtener el generador de clases. MFC busca en la lista de fábrica de clase asociada a este módulo y lo devuelve.  
  
5. Se llama a `COleObjectFactory::XClassFactory2::CreateInstance`. Antes de crear el objeto y el restablecimiento, esta función establece el estado del módulo en el estado del módulo que era el actual en el paso 3 (que era el actual cuando el `COleObjectFactory` se creara una instancia). Esto se realiza dentro de [METHOD_PROLOGUE](com-interface-entry-points.md).  
  
6.  Cuando se crea el objeto, es demasiado un `CCmdTarget` derivado y de la misma manera `COleObjectFactory` recuerda que el estado módulo estaba activo, y esto hace que el nuevo objeto. Ahora el objeto sabe qué estado del módulo para cambiar a cada vez que se llama.  
  
7.  El cliente llama a una función en el objeto OLE y COM que recibió de su `CoCreateInstance` llamar. Cuando se llama al objeto utiliza `METHOD_PROLOGUE` para cambiar el estado del módulo igual que `COleObjectFactory` does.  
  
 Como puede ver, el estado del módulo se propaga desde el objeto al objeto que se crean. Es importante que establezca correctamente el estado del módulo. Si no se establece, el archivo DLL o un objeto COM puede interactuar mal con una aplicación MFC que llama, o puede ser no se puede encontrar sus propios recursos o puede producir un error de otras maneras miserable.  
  
 Tenga en cuenta que ciertos tipos de archivos DLL, específicamente "De extensión de MFC" DLL no cambiará el estado del módulo en sus `RawDllMain` (en realidad, normalmente no incluso tienen un `RawDllMain`). Esto es porque están diseñados para comportarse "como si" fueran realmente presentes en la aplicación que los usa. Son mucho una parte de la aplicación que se está ejecutando y es su intención de modificar el estado global de la aplicación.  
  
 Controles OLE y otros archivos DLL es muy diferente. ¿Desea modificar el estado de la aplicación que realiza la llamada; la aplicación que llama a ellos no puede ser incluso una aplicación MFC y por lo que no puede haber ningún estado para modificar. Este es el motivo que se inventaron el cambio de estado de módulo.  
  
 Para las funciones exportadas desde un archivo DLL, como uno que se abre un cuadro de diálogo en el archivo DLL, debe agregar el código siguiente al principio de la función:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState())  
```  
  
 Con ello intercambia el estado actual del módulo con el estado devuelto desde [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) hasta el final del ámbito actual.  
  
 Problemas con los recursos en archivos DLL se producen si no se utiliza la macro AFX_MODULE_STATE. De forma predeterminada, MFC usa el identificador de recurso de la aplicación principal para cargar la plantilla de recursos. Esta plantilla se almacena realmente en el archivo DLL. La causa es que la información de estado de módulo de MFC no se ha cambiado, mediante la macro AFX_MODULE_STATE. El identificador de recurso se recupera del estado del módulo de MFC. Si no se cambia el estado del módulo hace que el identificador de recursos incorrecto para usarse.  
  
 AFX_MODULE_STATE no es necesario para colocarse en cada función del archivo DLL. Por ejemplo, `InitInstance` puede llamarse mediante el código MFC de la aplicación sin AFX_MODULE_STATE porque MFC cambia automáticamente el estado del módulo antes de `InitInstance` y, a continuación, los conmutadores de nuevo después de `InitInstance` devuelve. Lo mismo puede decirse de todos los controladores de mapa de mensajes. Archivos DLL de MFC estándar tiene en realidad un procedimiento de ventana maestro que cambia automáticamente el estado del módulo antes de enrutar cualquier mensaje.  
  
## <a name="process-local-data"></a>Procesamiento de datos Local  
 Procesamiento de datos local no sería de este tipo nos preocupamos por TI no hubiera para la dificultad del modelo Win32s DLL. En Win32s todos los archivos DLL comparten sus datos globales, incluso cuando la carga entre varias aplicaciones. Esto es muy diferente en el modelo de datos del archivo DLL para Win32 "real", donde cada DLL Obtiene una copia independiente de su espacio de datos en cada proceso que se conecta al archivo DLL. Para agregar a la complejidad, datos que se asignan en el montón en un archivo DLL Win32s están en realidad proceso específico (al menos en cuanto sale de la propiedad). Tenga en cuenta los datos y el código siguiente:  
  
```  
static CString strGlobal; // at file scope  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz,
    size_t cb)  
{  
    StringCbCopy(lpsz,
    cb,
    strGlobal);

}  
```  
  
 Tenga en cuenta lo que sucede si el código anterior esté en un archivo DLL y que se carga el archivo DLL mediante dos procesos A y B (de hecho, podría tener dos instancias de la misma aplicación). Una de las llamadas `SetGlobalString("Hello from A")`. Como resultado, se le asigna memoria la `CString` datos en el contexto del proceso de r. tenga en cuenta que el `CString` propio es global y es visible para ambos A y B. Ahora se llama B `GetGlobalString(sz, sizeof(sz))`. B podrán ver los datos que un conjunto. Esto es porque Win32s no proporciona ninguna protección entre los procesos como hace de Win32. Es el primer problema; en muchos casos no es conveniente que una aplicación afecta a los datos globales que se consideran que la propiedad de una aplicación diferente.  
  
 Hay también otros problemas adicionales. Supongamos que ahora se cierra. Cuando se cierra un, la memoria utilizada por la '`strGlobal`' cadena estará disponible para el sistema, es decir, se libera automáticamente toda la memoria asignada por un proceso por el sistema operativo. No se libera porque los `CString` se llama a destructor; no se ha llamado todavía. Libere simplemente porque la aplicación que lo asignó ha abandonado la escena. Ahora, si llama a B `GetGlobalString(sz, sizeof(sz))`, no se puede obtener datos válidos. Puede que otra aplicación ha utilizado esa memoria para otra cosa.  
  
 Claramente que exista un problema. MFC 3.x utiliza una técnica denominada almacenamiento local de subprocesos (TLS). MFC 3.x asignaría un índice TLS que en Win32s realmente actúa como un índice de almacenamiento local de proceso, incluso si no se llama que y, a continuación, hacer referencia a todos los datos basándose en ese índice TLS. Esto es similar al índice TLS que se utiliza para almacenar datos locales del subproceso en Win32 (vea a continuación para obtener más información acerca de ese tema). Esto debe cada DLL de MFC utilizar al menos dos índices TLS por proceso. Cuando se tiene en cuenta DLL de carga muchos OLE Control (OCX), rápidamente ejecutar fuera de los índices TLS (existen solo 64). Además, MFC tenía que coloque todos estos datos en un solo lugar, en una única estructura. No era muy extensible y no era ideal con respecto a su uso de índices TLS.  
  
 MFC 4.x soluciona este problema con un conjunto de plantillas de clase puede "ajustarse" los datos que deben ser el proceso local. Por ejemplo, podría corregirse el problema mencionado anteriormente escribiendo:  
  
```  
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
  
 MFC implementa en dos pasos. En primer lugar, hay una capa por encima de Win32 **Tls\***  API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, etc.) que usar solo dos índices TLS por proceso, independientemente de cuántos archivos DLL que tiene. Segundo, el `CProcessLocal` plantilla se proporciona para tener acceso a estos datos. Invalida el operador -> que es lo que permite la sintaxis intuitiva que se ven arriba. Todos los objetos que están encapsulados por `CProcessLocal` debe derivarse de `CNoTrackObject`. `CNoTrackObject` Proporciona un asignador de nivel inferior (**LocalAlloc**/**LocalFree**) y un destructor virtual que MFC puede destruir automáticamente los objetos locales de proceso cuando finaliza el proceso. Estos objetos pueden tener un destructor personalizado si es necesaria realizar una limpieza adicional. El ejemplo anterior no requiere una de ellas, ya que el compilador generará un destructor predeterminado para destruir el objeto incrustado `CString` objeto.  
  
 Hay otras ventajas de este enfoque interesantes. No solo son todos `CProcessLocal` objetos que se destruyen automáticamente, no se crea hasta que se necesiten. `CProcessLocal::operator->` creará una instancia del objeto asociado la primera vez que se llama y no antes del día. En el ejemplo anterior, esto significa que el '`strGlobal`' cadena no se creará hasta la primera vez que `SetGlobalString` o `GetGlobalString` se llama. En algunos casos, esto puede ayudar a reducir el tiempo de inicio DLL.  
  
## <a name="thread-local-data"></a>Datos locales de subproceso  
 Similar al procesar los datos locales, los datos locales de subproceso se usan cuando los datos deben ser locales para un subproceso determinado. Es decir, se necesita una instancia independiente de los datos para cada subproceso que tiene acceso a esos datos. Esto se muchas veces puede utilizar en lugar de los mecanismos de sincronización de una amplia. Si no necesita los datos debe ser compartida por varios subprocesos, estos mecanismos pueden ser costoso e innecesarios. Supongamos que ha surgido un `CString` objeto (muy como en el ejemplo anterior). Podemos hacerlo de subprocesos locales incluyéndolo con un `CThreadLocal` plantilla:  
  
```  
struct CMyThreadData : public CNoTrackObject  
{  
    CString strThread;  
};  
CThreadLocal<CMyThreadData> threadData;  
 
void MakeRandomString()  
{ *// a kind of card shuffle (not a great one)  
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
  
 Si `MakeRandomString` se llamó desde dos subprocesos diferentes, cada uno de ellos se "selección aleatoria de" la cadena de maneras diferentes sin interferir con las demás. Esto es porque no hay realmente una `strThread` instancia por subproceso en lugar de una sola instancia global.  
  
 Tenga en cuenta cómo se utiliza una referencia para capturar el `CString` dirección una vez en lugar de una vez por cada iteración del bucle. El código del bucle se han escrito con `threadData->strThread` everywhere '`str`' se usa, pero el código sería mucho más lento en ejecución. Es mejor para almacenar en caché una referencia a los datos cuando se producen tales referencias en bucles.  
  
 El `CThreadLocal` plantilla de clase utiliza los mismos mecanismos que `CProcessLocal` no y las mismas técnicas de implementación.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

