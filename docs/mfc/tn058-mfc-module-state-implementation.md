---
title: "TN058: Implementaci&#243;n de estado del m&#243;dulo MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.implementation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], estados de módulos"
  - "MFC [C++], administrar datos de estado"
  - "estados de módulos [C++], administrar datos de estado"
  - "estados de módulos [C++], conmutación"
  - "estado de proceso [C++]"
  - "estado de subproceso [C++]"
  - "TN058"
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN058: Implementaci&#243;n de estado del m&#243;dulo MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota técnica describe la implementación de “de construcciones estado de módulo” MFC.  Una descripción de la implementación de estado del módulo es fundamental para utilizar archivos DLL compartidos MFC DLL \(o servidor en proceso OLE\).  
  
 Antes de leer esta nota, hace referencia a “administrar los datos de estado de los módulos MFC” en [Crear documentos de Nuevo, Windows, y vistas](../mfc/creating-new-documents-windows-and-views.md).  Este artículo contiene información importante de uso e información general sobre este asunto.  
  
## Información general  
 Hay tres tipos de información de estado de MFC: Estado del módulo, estado de proceso, y estado de subproceso.  Estos tipos de estado se pueden combinar a veces.  Por ejemplo, los mapas del identificador de MFC son locales del módulo y local de subproceso.  Esto permite que dos módulos diferentes tienen diferentes mapas en cada uno de los subprocesos.  
  
 El estado de proceso y el estado de subproceso son similares.  Estos elementos de datos son cosas que han sido normalmente variables globales, pero tienen deben específicos de un proceso o un subproceso determinado para la compatibilidad adecuada de Win32s o para la compatibilidad adecuada de multithreading.  Qué categoría un elemento de datos determinado encaja depende de ese elemento y de la semántica deseada con respecto a los límites de procesos y subprocesos.  
  
 El estado del módulo es única en que puede contener el estado realmente global o decirla que es local de proceso o locales de subproceso.  Además, puede intercambiar rápidamente.  
  
## La conmutación del estado del módulo  
 Cada subproceso contiene un puntero a la “actual” o el estado “activo” de módulo \(naturalmente, el puntero es parte del estado local de subproceso MFC\).  Este puntero se cambia cuando el subproceso de ejecución pasa un límite de módulo, como una llamada de la aplicación en un control OLE o DLL, o una llamada al control OLE recién dentro de una aplicación.  
  
 Llamando a cambiar al estado actual del módulo **AfxSetModuleState**.  En general, nunca se tratará directamente de la API.  MFC, en muchos casos, lo llamará automáticamente \(en WinMain, los entrada\- puntos de OLE, **AfxWndProc**, etc.\). Esto se hace en cualquier componente que escriba vincular estáticamente en **WndProc**especial, y `WinMain` especial \(o `DllMain`\) que sabe que el estado del módulo debe ser actual.  Puede ver este código examinando DLLMODUL.CPP o APPMODUL.CPP en el directorio de MFC\\SRC.  
  
 Es raro que desea establecer el estado del módulo y después para no establecer posterior.  La mayoría de las veces se desea “insertar” dispone el estado de módulo como la actual y después, cuando se necesitan, “haga extrae” revertir original del contexto.  Esto se hace por [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) macro y la clase especial **AFX\_MAINTAIN\_STATE**.  
  
 `CCmdTarget` tiene características especiales para admitir pasar del estado del módulo.  En particular, `CCmdTarget` es la clase raíz utilizada para los puntos COM de automatización OLE y de entrada OLE.  Como cualquier otro punto de entrada expuesto al sistema, estos puntos de entrada deben establecer el estado de módulo correcto.  ¿Cómo `CCmdTarget` determinado conoce cuál debería ser el estado “correcta de módulo”?  La respuesta es que “recuerda” cuál el estado “actual” del módulo es cuando se construye, de modo que puede establecer el estado actual del módulo a ese valor “recordado” cuando se denomina más adelante.  Como resultado, el estado del módulo que un objeto especificado de `CCmdTarget` está asociado a es el estado del módulo que era actual en que el objeto se creó.  Toma un ejemplo simple de cargar un servidor INPROC, crear un objeto, y de llamar a sus métodos.  
  
1.  DLL lo cargue OLE mediante **LoadLibrary**.  
  
2.  **RawDllMain** se llama primero.  Establece el estado del módulo al estado estático conocida de módulo de DLL.  Por esta razón **RawDllMain** se vincula estáticamente al archivo DLL.  
  
3.  Se llama al constructor del generador de la clase asociada al objeto.  `COleObjectFactory` se deriva de `CCmdTarget` como resultado, recuerda en el estado del módulo se ha creado instancias.  Esto es importante — cuando el generador de clases se pide crear objetos, ahora sabe qué estado de módulo para crear la actual.  
  
4.  `DllGetClassObject` se denomina para obtener el generador de clases.  MFC busca en la lista de generador de clases asociada a este módulo y la devuelve.  
  
5.  Se llama**COleObjectFactory::XClassFactory2::CreateInstance** .  Antes de crear el objeto y de devolverlo, esta función establece el estado del módulo al estado del módulo que era actual en el paso 3 \(el que era actual en que `COleObjectFactory` creado instancias\).  Esto se hace dentro de [METHOD\_PROLOGUE](../Topic/METHOD_PROLOGUE.md).  
  
6.  Cuando se crea el objeto, también es un derivado de `CCmdTarget` y de la misma manera `COleObjectFactory` recordado que el estado del módulo estaba activo, lo hace este nuevo objeto.  Ahora el objeto sabe que el estado de módulo a cambiar siempre que se denomina.  
  
7.  El cliente llama a una función en el objeto COM OLE que recibió de la llamada de `CoCreateInstance` .  Cuando se llama al objeto utiliza `METHOD_PROLOGUE` para cambiar al estado del módulo igual que hace `COleObjectFactory` .  
  
 Como puede ver, propagan al estado del módulo de objeto al objeto cuando se crean.  Es importante tener el estado del módulo establecida correctamente.  Si no se establece, DLL o el objeto COM puede interactuar incorrectamente en una aplicación MFC que se está llamando, o no pueda encontrar los recursos propios, o puede producir un error de otras maneras desgraciadas.  
  
 Observe que algunos tipos de archivos DLL “, los archivos DLL de extensión MFC” no intercambian específicamente al estado del módulo en el **RawDllMain** \(realmente, ni siquiera normalmente tienen **RawDllMain**\).  Esto es porque los pensados para comportarse “como si” sean realmente presentes en la aplicación que los utiliza.  Son gran parte de la aplicación que está ejecutando y es su intención modificar que el estado global de la aplicación.  
  
 Controles OLE y otros archivos DLL son muy diferentes.  No desea modificar el estado de la aplicación de llamada; la aplicación que se está llamando puede no tiene que ser una aplicación MFC y por tanto no puede ser ninguna estado a modificar.  Esta es la razón que la conmutación del estado del módulo se inventado.  
  
 Para las funciones exportadas desde el archivo DLL, como uno que inicia un cuadro de diálogo en un archivo DLL, necesita agregar el código siguiente al principio de la función:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 Esto cambia al estado actual del módulo con el estado devuelto de [AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md) hasta el final del ámbito actual.  
  
 Los problemas con recursos en archivos DLL aparecerán si la macro de `AFX_MODULE_STATE` no se utiliza.  De forma predeterminada, MFC utiliza el identificador de recursos de la aplicación principal para cargar la plantilla de recursos.  Esta plantilla se almacena realmente en el archivo DLL.  La principal causa es que la información de estado del módulo MFC no ha sido intercambiada por la macro de `AFX_MODULE_STATE` .  El identificador de recursos se recupera del estado del módulo de MFC.  No cambiar el estado de módulo hace que el identificador de recursos incorrecto que se utilizará.  
  
 `AFX_MODULE_STATE` no necesita estar en cada función en el archivo DLL.  Por ejemplo, `InitInstance` puede llamar al código MFC en la aplicación sin `AFX_MODULE_STATE` MFC se desplaza automáticamente al estado del módulo antes de `InitInstance` y de modificadores se vuelve después de que `InitInstance` vuelva.  Lo mismo se aplica a todos los controladores del mapa de mensajes.  Los archivos DLL estándar incluyen realmente un procedimiento de ventana principal especial que automáticamente cambie el estado del módulo antes de enviar cualquier mensaje.  
  
## Datos locales de proceso  
 Los datos locales de proceso no se de tal gran interés de no ser por la dificultad del modelo de Win32s DLL.  En Win32s todos los archivos DLL comparten los datos globales, incluso cuando se cargan con varias aplicaciones.  Esto es muy diferente del modelo de datos “real” de un archivo DLL para Win32, donde cada DLL obtiene una copia independiente del espacio de datos en cada proceso que asocia al archivo DLL.  Para agregar a la complejidad, los datos asignado en el montón en Win32s DLL es de hecho específico de proceso \(al menos por lo que va la propiedad\).  Considere los datos y código siguientes:  
  
```  
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
  
 Considere lo que sucede si el código anterior en se encuentra en un archivo DLL y ese archivo DLL lo cargue dos procesos A y b \(podría, de hecho, ser dos instancias de la misma aplicación\).  Llamadas `SetGlobalString("Hello from A")`.  Como resultado, la memoria se asigna para los datos de `CString` en el contexto del proceso En.  Tenga presente que `CString` propio es global y está visible a y b.  Ahora llamadas `GetGlobalString(sz, sizeof(sz))`b.  B podrá ver los datos que A establecida.  Esto es porque hace Win32s no ofrece protección entre procesos Win32.  Es el primer problema; en muchos casos no es deseable tener un datos global de la influencia de la aplicación que se considere ser propiedad de otra aplicación.  
  
 Hay problemas adicionales también.  Supongamos que ahora sale A.  Cuando sale A, la memoria utilizada por la cadena de '`strGlobal`' está disponible para el sistema \(es decir, toda la memoria asignada por procesa A es libera automáticamente el sistema operativo.  No se libera porque se está llamando `CString` destructor; no se ha llamado todavía.  Se libera simplemente porque la aplicación que la asignada ha dejado de la escena.  Ahora si b denominado `GetGlobalString(sz, sizeof(sz))`, puede no obtener datos válidos.  Otra aplicación haya utilizado esa memoria para el algo más.  
  
 Un problema existe claramente.  MFC 3.x utiliza una técnica denominada almacenamiento local de subprocesos \(TLS\).  MFC 3.x afectaría asigne un índice de TLS que bajo Win32s actúa realmente como índice de almacenamiento de proceso local, aunque no se denomina que y después hacer referencia a todos los datos basados en el índice de TLS.  Esto es similar al índice de TLS utilizado para almacenar datos de subproceso\- local en Win32 \(vea a continuación para obtener más información sobre ese asunto\).  Esto hizo que cada archivo DLL de MFC utilizado por lo menos dos índices de TLS por proceso.  Cuando se explica cargar muchos archivos DLL de controles activex \(OCXs\), se ejecuta rápidamente con los índices de TLS \(solo hay 64 disponible\).  Además, MFC tenía que colocar todo estos datos en un lugar, en una única estructura.  No es muy extensible y no es ideal con respecto al uso de los índices de TLS.  
  
 MFC 4.x soluciona esta con un conjunto de plantillas de clase que puede “ajustar” alrededor de los datos que deben ser local de proceso.  Por ejemplo, el problema mencionado anteriormente podría corregir escribiendo:  
  
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
  
 MFC implementa esto en dos pasos.  Primero, hay un nivel superior de Win32 **Tls\*** API \(**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, etc.\) que utilizan sólo dos índices de TLS por proceso, independientemente de cuántos archivos DLL se tienen.  En segundo lugar, la plantilla de `CProcessLocal` se proporciona para tener acceso a estos datos.  Reemplaza el operador\> que lo que permite la sintaxis intuitiva que ve anteriormente.  Todos los objetos que no se ajustan por `CProcessLocal` se deben derivar de `CNoTrackObject`.  `CNoTrackObject` proporciona un asignador de nivel inferior \(**LocalAlloc**\/**LocalFree**\) y el destructor virtual tales que MFC puede automáticamente destruir los objetos locales de proceso cuando finaliza el proceso.  Estos objetos pueden tener un destructor personalizado si se requiere la limpieza adicional.  En el ejemplo anterior no requiere uno, puesto que el compilador generará un valor predeterminado destructor para destruir el objeto incrustado de `CString` .  
  
 Hay otras ventajas interesantes a este enfoque.  No solo todos los objetos de `CProcessLocal` se destruyen automáticamente, no se crean hasta que se necesitan.  `CProcessLocal::operator->` creará una instancia del objeto asociado la primera vez que se llama, y no antes.  En el ejemplo anterior, que significa que la cadena de '`strGlobal`' no se construida hasta la primera vez **SetGlobalString** o **GetGlobalString** se denomina.  A veces, esto puede ayudar a reducir el tiempo de inicio del archivo DLL.  
  
## Datos locales de subproceso  
 Similar a los datos locales de proceso, datos locales de subproceso se utiliza cuando los datos deben ser local de un subproceso dado.  Es decir, necesita una instancia independiente de los datos para cada subproceso que acceso esos datos.  Esto se puede muchas veces usar en lugar de mecanismos extensos de sincronización.  Si los datos no necesita ser compartidos por varios subprocesos, estos mecanismos pueden resultar costoso e innecesarios.  Suponga que teníamos un objeto de `CString` \(como el ejemplo anterior\).  Podemos hacerlo el valor local de subproceso encapsulándola con una plantilla de `CThreadLocal` :  
  
```  
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
      randErr = rand_s( &randomNumber );  
      if ( randErr == 0 )  
      {  
         TCHAR ch = randomNumber % 52 + 1;  
         if (str.Find(ch) < 0)  
            str += ch; // not found, add it  
      }  
   }  
}  
```  
  
 Si `MakeRandomString` se denomina de dos subprocesos diferentes, cada uno “mezclaría” la cadena de maneras diferentes sin interferir con otra.  Esto es porque existe una instancia de `strThread` por el subproceso en lugar de solo una instancia global.  
  
 Nota en lugar de cómo una referencia se utiliza para capturar la dirección de `CString` una vez una vez por iteración del bucle.  Se utiliza el código de bucle podría haberse escribir con `threadData->strThread` en todas partes '`str`' , pero el código sería mucho más lenta a la ejecución.  Es mejor almacenar en memoria caché una referencia a los datos cuando dichas referencias aparecen en bucles.  
  
 La plantilla de clase `CThreadLocal` utiliza los mismos mecanismos que `CProcessLocal` realiza y las mismas técnicas de implementación.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)