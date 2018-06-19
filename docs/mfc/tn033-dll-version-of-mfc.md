---
title: 'TN033: Versión de DLL de MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dll
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a247ffc36b3e0eb3e52c6f04949c693597d73064
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385247"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: Versión de DLL de MFC
Esta nota describe cómo se puede utilizar el compartidas MFCxx.DLL y MFCxxD.DLL (donde x es el número de versión MFC) bibliotecas de vínculos dinámicos con aplicaciones MFC y archivos DLL de extensión MFC. Para obtener más información sobre archivos DLL de MFC estándar, consulte [utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).  
  
 Esta nota técnica abarca tres aspectos de la DLL. Las dos últimas son para los usuarios más avanzados:  
  
- [Cómo crear un archivo DLL de extensión de MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)  
  
- [Cómo crear una aplicación MFC que utiliza la versión del archivo DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)  
  
- [Cómo la MFC comparte bibliotecas de vínculos dinámicos se implementan](#_mfcnotes_how_the_mfc30.dll_is_implemented)  
  
 Si está interesado en la creación de un archivo DLL mediante MFC que puede usarse con aplicaciones no están basados en MFC (Esto se denomina una DLL de MFC normal), consulte [Nota técnica 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).  
  
## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Información general de soporte técnico de MFCxx.DLL: archivos y terminología  
 **DLL de MFC regular**: usar una DLL de MFC normal para generar un archivo DLL independiente con algunas de las clases MFC. A través del límite de aplicación/DLL interfaces son de "C" y la aplicación cliente no tiene que ser una aplicación MFC.  
  
 Se trata de la versión de compatibilidad con DLL de MFC 1.0 admitido. Se describe en [Nota técnica 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) y el ejemplo de conceptos avanzados de MFC [DLLScreenCap](../visual-cpp-samples.md).  
  
> [!NOTE]
>  A partir de Visual C++ versión 4.0, el término **USRDLL** está obsoleto y se ha reemplazado por un DLL de MFC normal que se vincula estáticamente a MFC. También puede generar a una DLL de MFC que se vincule dinámicamente a MFC normal.  
  
 MFC 3.0 (y versiones posteriores) es compatible con archivos DLL de MFC estándar con todas las nuevas funcionalidades incluidas las clases de base de datos y OLE.  
  
 **AFXDLL**: Esto también se conoce como la versión compartida de MFC (bibliotecas). Se trata de la nueva compatibilidad con DLL agregado en MFC 2.0. La propia biblioteca MFC es un número de archivos DLL (descritos a continuación) y una aplicación cliente o el archivo DLL se vincula dinámicamente los archivos DLL que requiere. Interfaces a través del límite de aplicación/DLL son C + / interfaces de clase MFC. La aplicación cliente debe ser una aplicación MFC. Esto es compatible con toda la funcionalidad de MFC 3.0 (excepción: no se admite UNICODE para las clases de base de datos).  
  
> [!NOTE]
>  A partir de la versión 4.0 de Visual C++, este tipo de archivo DLL se conoce como un "archivo DLL de extensión."  
  
 Esta nota usará MFCxx.DLL para hacer referencia a todo el conjunto de DLL de MFC, que incluye:  
  
-   Depuración: MFCSxxD.LIB (estático) y MFCxxD.DLL (combinados).  
  
-   Versión: MFCxx.DLL (combinada) y MFCSxx.LIB (estático).  
  
-   Depuración de Unicode: MFCxxUD.DLL (combinada) y MFCSxxD.LIB (estático).  
  
-   Versión de Unicode: MFCxxU.DLL (combinada) y MFCSxxU.LIB (estático).  
  
> [!NOTE]
>  El MFCSxx [U] [D]. Lib se utiliza en junto con la MFC archivos DLL compartidos. Estas bibliotecas contienen código que debe vincularse estáticamente a la aplicación o el archivo DLL.  
  
 Una aplicación estará vinculada a las bibliotecas de importación correspondiente:  
  
-   Depurar: MFCxxD.LIB  
  
-   Versión: MFCxx.LIB  
  
-   Depuración de Unicode: MFCxxUD.LIB  
  
-   Versión de Unicode: MFCxxU.LIB  
  
 Una "DLL de extensión de MFC" es un archivo DLL compilado en MFCxx.DLL (y/o la MFC otra archivos DLL compartidos). Aquí la arquitectura de componentes MFC se inicia. Si se derive una clase útil de una clase MFC o generar otro kit de herramientas de MFC similar, puede colocarlo en un archivo DLL. Que el archivo DLL utiliza MFCxx.DLL, igual que la aplicación cliente ultimate. Esto permite a clases de hoja reutilizables, clases base reutilizables y clases de documento/vista reutilizables.  
  
## <a name="pros-and-cons"></a>Ventajas y desventajas  
 ¿Por qué se debe usar la versión compartida de MFC  
  
-   Usa la biblioteca compartida puede dar lugar a que las aplicaciones más pequeñas (una aplicación mínima que utiliza la mayor parte de la biblioteca MFC es menor que 10K).  
  
-   La versión compartida de MFC es compatible con archivos DLL de extensión de MFC y archivos DLL de MFC estándar.  
  
-   Crear una aplicación que utiliza las bibliotecas compartidas de MFC es más rápido que crear una aplicación MFC vinculada estáticamente porque no es necesario vincular MFC. Esto es especialmente cierto en **depurar** compilaciones donde el vinculador debe compactar la información de depuración, al vincular con un archivo DLL que ya contiene la información de depuración, hay menos información de depuración para compactar dentro de la aplicación.  
  
 ¿Por qué no debe utilizarse la versión compartida de MFC:  
  
-   Una aplicación que utiliza la biblioteca compartida de envío requiere que incluyen MFCxx.DLL (y otros) biblioteca con el programa. MFCxx.DLL es puede redistribuir libremente como muchos archivos DLL, pero todavía debe instalar la DLL en el programa de instalación. Además, debe distribuir la MSVCRTxx.DLL, que contiene la biblioteca en tiempo de ejecución de C que se está usando el programa y los mismos archivos DLL de MFC.  
  
##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Cómo escribir un archivo DLL de extensión MFC  
 Una DLL de extensión de MFC es un archivo DLL que contiene las clases y funciones escritas para adornar la funcionalidad de las clases MFC. Una DLL de extensión de MFC utiliza los archivos DLL de MFC compartida de la misma manera que una aplicación utiliza, con unas consideraciones adicionales:  
  
-   El proceso de compilación es similar a crear una aplicación que utiliza las bibliotecas compartidas de MFC con unos cuantos más opciones del compilador y del vinculador.  
  
-   Una DLL de extensión de MFC no tiene un `CWinApp`-clase derivada.  
  
-   Una DLL de extensión de MFC debe proporcionar una clase especial `DllMain`. AppWizard proporciona una `DllMain` función que se puede modificar.  
  
-   Una DLL de extensión de MFC suelen proporcionar una rutina de inicialización para crear un **CDynLinkLibrary** si desea que un archivo DLL de la extensión MFC exportar `CRuntimeClass`es o recursos para la aplicación. Una clase derivada de **CDynLinkLibrary** puede utilizarse si se deben mantener los datos según la aplicación mediante el archivo DLL de extensión MFC.  
  
 Estas consideraciones se describen con más detalle a continuación. También se debe hacer referencia en el ejemplo de conceptos avanzados de MFC [DLLHUSK](../visual-cpp-samples.md) desde que muestra:  
  
-   Compilar una aplicación mediante las bibliotecas compartidas. (DLLHUSK. EXE es una aplicación MFC que se vincule dinámicamente a las bibliotecas MFC, así como otros archivos DLL).  
  
-   Creación de un archivo DLL de extensión MFC. (Tenga en cuenta las marcas especiales como `_AFXEXT` que se usan en la creación de un archivo DLL de extensión MFC)  
  
-   Dos ejemplos de archivos DLL de extensión de MFC. Una muestra la estructura básica de una DLL de extensión de MFC con exportaciones limitadas (TESTDLL1) y la otra muestra exportar una interfaz de clase completa (TESTDLL2).  
  
 La aplicación cliente y los archivos DLL de extensión MFC debe usar la misma versión de MFCxx.DLL. Debe seguir la convención de DLL de MFC y proporcionar una depuración y minorista (/ versión) versión de la DLL de extensión MFC. Esto permite a los programas de cliente para generar versiones de depuración y comerciales de sus aplicaciones y vincularlas con la depuración adecuados o una versión comercial de todos los archivos DLL.  
  
> [!NOTE]
>  Dado que C++ nombre alteración y problemas de exportación, la lista de exportación de un archivo DLL de extensión MFC puede ser distinta en las versiones de depuración y comerciales del mismo archivo DLL y los archivos DLL de distintas plataformas. La versión comercial MFCxx.DLL ha aproximadamente 2.000 puntos de entrada exportados; la depuración MFCxxD.DLL ha exportado 3000 unos puntos de entrada.  
  
### <a name="quick-note-on-memory-management"></a>Nota rápida en administración de memoria  
 La sección titulada "Administración de memoria", casi al final de esta nota técnica, describe la implementación de MFCxx.DLL con la versión compartida de MFC. La información que necesita saber para implementar solo una extensión MFC que dll se describe aquí.  
  
 MFCxx.DLL y todas las DLL de extensión MFC cargadas en el espacio de direcciones de la aplicación cliente usará el mismo asignador de memoria, la carga de recursos y otros Estados "globales" de MFC como si estuvieran en la misma aplicación. Esto es importante porque las bibliotecas DLL que no son de MFC y archivos DLL de MFC estándar vinculados estáticamente a MFC realizan funciones exactamente opuestas y cada sus archivos DLL asigna fuera de su propio bloque de memoria.  
  
 Si un archivo DLL de extensión MFC asigna memoria, esta memoria puede combinarse libremente con cualquier otro objeto asignado por la aplicación. Además, si se bloquea una aplicación que usa las bibliotecas compartidas de MFC, la protección del sistema operativo mantendrá la integridad de cualquier otra aplicación MFC que comparta el archivo DLL.  
  
 De forma similar, otros Estados "globales" de MFC, como el archivo ejecutable actual que se cargan recursos, también se comparten entre la aplicación cliente y todos los archivos DLL de extensión MFC, así como MFCxx.DLL propio.  
  
### <a name="building-an-mfc-extension-dll"></a>Creación de un archivo DLL de extensión MFC  
 Puede usar el Asistente para aplicaciones para crear un proyecto de DLL de extensión MFC, y generará automáticamente el compilador adecuada y la configuración del vinculador. Era generar también un `DllMain` función que se puede modificar.  
  
 Si va a convertir un proyecto existente a un archivo DLL de extensión MFC, comience con las reglas estándares para la creación de una aplicación utilizando la versión compartida de MFC, a continuación, haga lo siguiente:  
  
-   Agregar **/D_AFXEXT** a los marcadores del compilador. En el cuadro de diálogo Propiedades del proyecto, seleccione el nodo C y C++. A continuación, seleccione la categoría de preprocesador. Agregar `_AFXEXT` al campo definir Macros, separando cada uno de los elementos con punto y coma.  
  
-   Quitar el **/Gy** modificador del compilador. En el cuadro de diálogo Propiedades del proyecto, seleccione el nodo C y C++. A continuación, seleccione la categoría de generación de código. Compruebe que no está habilitada la opción "Habilitar vinculación en el nivel de función". Así resultará más fácil exportar clases porque el vinculador no quitará las funciones. Si el proyecto original se utiliza para compilar normal MFC DLL vinculados estáticamente a MFC, cambiar el **/MT [d]** opción de compilador **/MD [d]**.  
  
-   Generar una biblioteca de exportación con la **/DLL** opción de vínculo. Esto se establecerá cuando se crea un nuevo destino, especificar la biblioteca de vínculos dinámicos Win32 como el tipo de destino.  
  
### <a name="changing-your-header-files"></a>Cambiar los archivos de encabezado  
 El objetivo de un archivo DLL de extensión MFC es normalmente exportar alguna funcionalidad común a una o varias aplicaciones que pueden usar esa funcionalidad. Esto se reduce a exportar las clases y funciones globales que están disponibles para las aplicaciones cliente.  
  
 Para ello debe asegurarse de que cada una de las funciones miembro se marca como importar o exportar según corresponda. Esto requiere declaraciones especiales: **__declspec (dllexport)** y **__declspec (dllimport)**. Cuando se utilizan las clases de las aplicaciones de cliente, que desea que se declara como **__declspec (dllimport)**. Cuando se está generando el propio archivo DLL de extensión de MFC, debe declararse como **__declspec (dllexport)**. Además, las funciones deben ser realmente exportadas, para que los programas de cliente se enlazan a ellos en tiempo de carga.  
  
 Para exportar toda la clase, use **AFX_EXT_CLASS** en la definición de clase. Esta macro se define mediante el marco de trabajo como **__declspec (dllexport)** cuando **_AFXDLL** y `_AFXEXT` está definido, pero se define como **__declspec (dllimport)** cuando `_AFXEXT` no está definido. `_AFXEXT` como se describió anteriormente, solo se define al crear el archivo DLL de extensión MFC. Por ejemplo:  
  
```  
class AFX_EXT_CLASS CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
### <a name="not-exporting-the-entire-class"></a>No exporte toda la clase  
 En ocasiones, puede que desee exportar solo los miembros individuales necesarios de la clase. Por ejemplo, si va a exportar una `CDialog`-clase derivada, solo deberá exportar el constructor y el `DoModal` llamar. Puede exportar a estos miembros mediante la DLL. Archivo DEF, pero también puede usar **AFX_EXT_CLASS** de la misma manera en los miembros individuales que desea exportar.  
  
 Por ejemplo:  
  
```  
class CExampleDialog : public CDialog  
{  
public:  
    AFX_EXT_CLASS CExampleDialog();
AFX_EXT_CLASS int DoModal();
*// rest of class definition  
 .  
 .  
 .  
};  
```  
  
 Al hacerlo, puede encontrarse con un problema adicional porque ya no se va a exportar a todos los miembros de la clase. El problema está en la forma en que funcionan las macros MFC. Algunas de las macros de aplicación auxiliar de MFC realmente declaran ni definen a miembros de datos. Por lo tanto, estos miembros de datos también necesitará que se exportarán desde el archivo DLL.  
  
 Por ejemplo, el `DECLARE_DYNAMIC` macro se define como sigue cuando se crea un archivo DLL de extensión MFC:  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
    static CRuntimeClass* PASCAL _GetBaseClass();

\  
    public: \  
    static AFX_DATA CRuntimeClass class##class_name; \  
    virtual CRuntimeClass* GetRuntimeClass() const;

\  
```  
  
 La línea que comienza "estático `AFX_DATA`" se declara como un objeto estático dentro de la clase. Para exportar correctamente esta clase y tener acceso a la información en tiempo de ejecución desde un cliente. EXE, tiene que exportar este objeto estático. Dado que el objeto estático se declara con el modificador `AFX_DATA`, basta con definir `AFX_DATA` como **__declspec (dllexport)** al generar el archivo DLL y defínalo como **__declspec (dllimport)** al generar el archivo ejecutable del cliente.  
  
 Tal y como se dijo anteriormente, **AFX_EXT_CLASS** ya está definida de esta manera. Solo tiene que volver a definir `AFX_DATA` a ser el mismo que **AFX_EXT_CLASS** alrededor de la definición de clase.  
  
 Por ejemplo:  
  
```  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
class CExampleView : public CView  
{  
    DECLARE_DYNAMIC() *// ... class definition ...  
};  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
 MFC siempre utiliza el `AFX_DATA` símbolos en elementos de datos define dentro de las macros, por lo que esta técnica funcionará para todos estos escenarios. Por ejemplo, funcionará para `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Si va a exportar toda la clase en lugar de los miembros seleccionados de la clase, se exportan automáticamente los miembros de datos estáticos.  
  
 Puede usar la misma técnica para exportar automáticamente la `CArchive` operador de extracción para las clases que utilizan el `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros. Exportar el operador de archivo encerrando las declaraciones de clase (ubicado en el. Archivo H) con el código siguiente:  
  
```  
#undef AFX_API  
#define AFX_API AFX_EXT_CLASS  
 
<your class declarations here>  
 
#undef AFX_API  
#define AFX_API  
```  
  
### <a name="limitations-of-afxext"></a>Limitaciones de _AFXEXT  
 Puede usar el _**AFXEXT** símbolo de preprocesador para la extensión MFC DLL siempre y cuando no tiene varios niveles de archivos DLL de extensión MFC. Si tiene archivos DLL que llamar o derivar desde clases de sus propios archivos DLL, que se derivan de las clases MFC, de extensión MFC de extensión de MFC debe utilizar su propio símbolo de preprocesador para evitar la ambigüedad.  
  
 El problema es que en Win32, debe declarar explícitamente los datos como **__declspec (dllexport)** si no se puede exportar desde un archivo DLL, y **__declspec (dllimport)** si se va a importar desde un archivo DLL. Cuando se define `_AFXEXT`, los encabezados de MFC Asegúrese de que **AFX_EXT_CLASS** se definió correctamente.  
  
 Si tiene varios niveles, un símbolo como **AFX_EXT_CLASS** no es suficiente, ya que un archivo DLL de extensión MFC puede exportar clases nuevas, así como importar otras clases desde otro archivo DLL de extensión MFC. Para solucionar este problema, utilice un símbolo de preprocesador especial que indique que está generando el archivo DLL, frente al uso de la DLL. Por ejemplo, imagine dos archivos DLL de extensión MFC,.dll y B.DLL. Cada uno de ellos exporta algunas clases en A.H y B.H, respectivamente. B.DLL utiliza las clases de.dll. Los archivos de encabezado sería algo parecido a esto:  
  
```  
/* A.H */  
#ifdef A_IMPL  
 #define CLASS_DECL_A   __declspec(dllexport)  
#else  
 #define CLASS_DECL_A   __declspec(dllimport)  
#endif  
 
class CLASS_DECL_A CExampleA : public CObject  
{ ... class definition ... };  
 
/* B.H */  
#ifdef B_IMPL  
 #define CLASS_DECL_B   __declspec(dllexport)  
#else  
 #define CLASS_DECL_B   __declspec(dllimport)  
#endif  
 
class CLASS_DECL_B CExampleB : public CExampleA  
{ ... class definition .. };  
```  
  
 .Dll se genera con **/D A_IMPL** y B.DLL se genera con **/D B_IMPL**. Si utiliza símbolos independientes para cada DLL, CExampleB se exporta y CExampleA se importa al generar B.dll. CExampleA se exporta al generar A.DLL y se importa al ser utilizada por B.DLL (o algún otro cliente).  
  
 No se puede realizar este tipo de distribución en capas cuando se usa la integrada **AFX_EXT_CLASS** y `_AFXEXT` símbolos de preprocesador. La técnica descrita anteriormente soluciona este problema de forma no al contrario que el mecanismo de MFC utiliza al generar su archivos DLL de extensión de MFC de la red, OLE y base de datos.  
  
### <a name="not-exporting-the-entire-class"></a>No exporte toda la clase  
 De nuevo, tendrá que tener especial cuidado cuando no se exporta una clase entera. Tiene que asegurarse de que los elementos de datos necesarios creados por las macros MFC se exportan correctamente. Esto puede hacerse mediante la definición de volver a **AFX_DATA** macro de la clase específica. Esto debe hacerse siempre que no se exporte toda la clase.  
  
 Por ejemplo:  
  
```  
// A.H  
#ifdef A_IMPL  
 #define CLASS_DECL_A  _declspec(dllexport)  
#else  
 #define CLASS_DECL_A  _declspec(dllimport)  
 #endif  
 
#undef  AFX_DATA  
#define AFX_DATA CLASS_DECL_A  
 
class CExampleA : public CObject  
{  
    DECLARE_DYNAMIC() 
    CLASS_DECL_A int SomeFunction();
*//class definition   
 .  
 .  
 .  
};  
 
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### <a name="dllmain"></a>DllMain  
 Éste es el código exacto que se debe colocar en el archivo de código fuente principal para el archivo DLL de extensión MFC. Que debe venir después de que incluye el estándar. Tenga en cuenta que cuando se usa el Asistente para aplicaciones para crear archivos de inicio para un archivo DLL de extensión MFC, proporciona un `DllMain` para usted.  
  
```  
#include "afxdllx.h"  
  
static AFX_EXTENSION_MODULE extensionDLL;  
  
extern "C" int APIENTRY   
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)  
{  
   if (dwReason == DLL_PROCESS_ATTACH)  
   {  
      // MFC extension DLL one-time initialization   
      if (!AfxInitExtensionModule(  
             extensionDLL, hInstance))  
         return 0;  
  
      // TODO: perform other initialization tasks here  
   }  
   else if (dwReason == DLL_PROCESS_DETACH)  
   {  
      // MFC extension DLL per-process termination  
      AfxTermExtensionModule(extensionDLL);  
  
          // TODO: perform other cleanup tasks here  
   }  
   return 1;   // ok  
}  
```  
  
 La llamada a `AfxInitExtensionModule` captura las clases en tiempo de ejecución de módulos (`CRuntimeClass` estructuras), así como los generadores de objetos (`COleObjectFactory` objetos) para su uso posterior cuando el **CDynLinkLibrary** se crea el objeto. La llamada (opcional) para `AfxTermExtensionModule` permite MFC limpiar el archivo DLL de extensión MFC cuando se desasocia de cada proceso (que se produce cuando termina el proceso, o cuando se descarga el archivo DLL como resultado de un **FreeLibrary** llamar) desde el archivo DLL de extensión MFC . Desde la mayoría no se cargan dinámicamente archivos DLL de extensión de MFC (normalmente, se vinculan a través de sus bibliotecas de importación), la llamada a `AfxTermExtensionModule` normalmente no es necesario.  
  
 Si la aplicación se carga y libera dinámicamente los archivos DLL de extensión MFC, no olvide llamar `AfxTermExtensionModule` como se indicó anteriormente. También asegúrese de usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de funciones de Win32 **LoadLibrary** y **FreeLibrary**) si la aplicación utiliza varios subprocesos o si carga dinámicamente a MFC archivo DLL de extensión. Usar `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y cierre que se ejecuta cuando se cargan y descargan el archivo DLL de extensión MFC no dañe el estado global de MFC.  
  
 El archivo de encabezado AFXDLLX. H contiene definiciones especiales para las estructuras utilizadas en archivos DLL de extensión MFC, como la definición de `AFX_EXTENSION_MODULE` y **CDynLinkLibrary**.  
  
 Global *extensionDLL* debe declararse como se muestra. A diferencia de la versión de 16 bits de MFC, puede asignar memoria y llamar a funciones MFC durante este tiempo, ya que MFCxx.DLL está totalmente inicializado en el momento en el `DllMain` se llama.  
  
### <a name="sharing-resources-and-classes"></a>Compartir recursos y clases  
 Archivos DLL de extensión MFC simples sólo necesitan exportar unas cuantas funciones de poco ancho de banda a la aplicación cliente y nada más. Más archivos DLL de uso intensivo de interfaz de usuario que desee exportar recursos y las clases de C++ a la aplicación cliente.  
  
 La exportación de recursos se realiza mediante una lista de recursos. En cada aplicación es una lista vinculada individualmente de **CDynLinkLibrary** objetos. Cuando busca un recurso, la mayoría de las implementaciones MFC estándar que cargan recursos buscan primera en el módulo de recursos actual (`AfxGetResourceHandle`) y no se ha encontrado el recorrido de la lista de **CDynLinkLibrary** objetos intenta cargar el recurso solicitado.  
  
 La creación dinámica de objetos de C++ le asigna un nombre de clase de C++ es similar. El mecanismo de deserialización de objetos de MFC requiere que todos de la `CRuntimeClass` objetos estén registrados para poder reconstruir creando dinámicamente objetos C++ del tipo requerido a partir de lo que estaba almacenado antes.  
  
 Si desea que la aplicación cliente para utilizar clases en el archivo DLL de extensión MFC que están `DECLARE_SERIAL`, será necesario exportar las clases para que sea visible para la aplicación de cliente. También se debe recorrer el **CDynLinkLibrary** lista.  
  
 En el caso del ejemplo de conceptos avanzados de MFC [DLLHUSK](../visual-cpp-samples.md), la lista es similar:  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
 |      |  
    TESTDLL2.DLL TESTDLL2.DLL  
 |      |  
    TESTDLL1.DLL TESTDLL1.DLL  
 |      |  
 |      |  
    MFC90D.DLL MFC90.DLL  
```  
  
 MFCxx.DLL es suele estar al final en el recurso y la lista de clases. MFCxx.DLL incluye todos los recursos MFC estándares, incluidas las cadenas para todos los identificadores de comando estándar. Colocar en la cola de la lista los archivos DLL y la aplicación cliente no tiene un su propia copia de los recursos MFC estándar, pero que se basan en los recursos compartidos de MFCxx.DLL en su lugar.  
  
 Combinar los recursos y los nombres de clase de todos los archivos DLL en el espacio de nombres de la aplicación cliente tiene la desventaja que tienes que tener cuidado qué identificadores o nombres que se puede seleccionar. Por supuesto puede deshabilitar esta característica mediante la exportación no cualquiera los recursos o una **CDynLinkLibrary** objeto a la aplicación cliente. El [DLLHUSK](../visual-cpp-samples.md) ejemplo administra el espacio de nombres de recurso compartido mediante varios archivos de encabezado. Vea [Nota técnica 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) para obtener más sugerencias sobre el uso de archivos de recursos compartidos.  
  
### <a name="initializing-the-dll"></a>Inicializar el archivo DLL  
 Como se mencionó anteriormente, normalmente es conveniente crear un **CDynLinkLibrary** objeto para que la exportación de los recursos y las clases a la aplicación cliente. Debe proporcionar un punto de entrada exportados para inicializar el archivo DLL. Como mínimo, se trata de una rutina void que no toma ningún argumento y no devuelve nada, pero puede ser que desee.  
  
 Cada aplicación de cliente que desea usar el archivo DLL debe llamar a esta rutina de inicialización, si se emplea este método. También puede asignar este **CDynLinkLibrary** objeto en su `DllMain` justo después de llamar a `AfxInitExtensionModule`.  
  
 La rutina de inicialización debe crear un **CDynLinkLibrary** objeto en el montón de la aplicación actual, conectado su información de archivo DLL de extensión de MFC. Esto puede hacerse con lo siguiente:  
  
```  
extern "C" extern void WINAPI InitXxxDLL()  
{  
    new CDynLinkLibrary(extensionDLL);

}  
```  
  
 El nombre de la rutina, *InitXxxDLL* en este ejemplo, puede ser que desee. No necesita ser `extern "C"`, pero lo hace así en la lista de exportación fácil de mantener.  
  
> [!NOTE]
>  Si utiliza el archivo DLL de extensión MFC desde una DLL de MFC normal, debe exportar esta función de inicialización. Esta función se debe invocar desde la DLL de MFC normal antes de utilizar las clases de archivo DLL de extensión MFC o recursos.  
  
### <a name="exporting-entries"></a>Exportar las entradas  
 Una manera sencilla de exportar las clases es usar **__declspec (dllimport)** y **__declspec (dllexport)** sobre cada clase y función global que se va a exportar. Esto resulta mucho más sencillo, pero es menos eficaz que nombre cada punto de entrada (se describe a continuación), ya que tiene menos control sobre qué funciones se exportan y no se puede exportar las funciones por ordinal. TESTDLL1 y TESTDLL2 utilizan este método para exportar sus entradas.  
  
 Un método más eficaz (y el método utilizado por MFCxx.DLL) consiste en exportar manualmente cada entrada de asignación de nombres a cada entrada de la. Archivo DEF. Puesto que nos estamos exportar exportaciones selectivas desde el archivo DLL (es decir, no todos los elementos), debemos decidir qué interfaces determinados que se va a exportar. Esto es difícil, ya que debe especificar los nombres alterados al vinculador en forma de entradas en el. Archivo DEF. No exporte las clases de C++, a menos que realmente necesita tener un vínculo simbólico para él.  
  
 Si ha intentado exportar C++ las clases con una. DEF archivar antes, puede desarrollar una herramienta para generar automáticamente esta lista. Esto puede hacerse mediante un proceso de dos fases vínculo. Vincular al archivo DLL una vez con ninguna exportación, y permite al vinculador que genere una. Archivo de asignación. El archivo. Archivo de asignación puede utilizarse para generar una lista de funciones que se deben exportar, por lo que con algunos reorganizar, se puede utilizar para generar las entradas de exportación para el. Archivo DEF. La lista de exportación para MFCxx.DLL y los archivos DLL de extensión de MFC de la base de datos, varios miles en número y OLE se generó con dicho proceso (aunque no es completamente automático y requiere algunos disponible para la optimización cada vez en unos instantes).  
  
### <a name="cwinapp-vs-cdynlinklibrary"></a>Frente a CWinApp CDynLinkLibrary  
 Una DLL de extensión de MFC no tiene un `CWinApp`-objeto proprio derivado; en su lugar debe funcionar con el `CWinApp`-deriva el objeto de la aplicación cliente. Esto significa que la aplicación cliente es propietaria del suministro principal de mensajes, el bucle de inactividad y así sucesivamente.  
  
 Si el archivo DLL de extensión de MFC requiere mantener datos adicionales para cada aplicación, puede derivar una nueva clase de **CDynLinkLibrary** y crearla en el InitXxxDLL rutina descritas anteriormente. Cuando se ejecuta, el archivo DLL puede comprobar la lista de la aplicación actual de **CDynLinkLibrary** objetos que se va a buscar el correspondiente a ese archivo DLL de extensión MFC determinado.  
  
### <a name="using-resources-in-your-dll-implementation"></a>Uso de recursos en su implementación de DLL  
 Como se mencionó anteriormente, la carga de recursos predeterminado le guiará a la lista de **CDynLinkLibrary** objetos busca el primer archivo EXE o DLL que tiene el recurso solicitado. Todas las API de MFC, así como todo el código interno usa `AfxFindResourceHandle` para recorrer la lista de recursos para buscar cualquier recurso, con independencia de dónde pueden residir.  
  
 Si desea que sólo necesita cargar recursos desde una ubicación específica, utilice las API `AfxGetResourceHandle` y `AfxSetResourceHandle` para guardar el identificador antiguo y establecer el nuevo identificador. Asegúrese de restaurar el identificador de recurso antiguo antes de volver a la aplicación de cliente. El ejemplo TESTDLL2 usa este enfoque para cargar explícitamente un menú.  
  
 Recorrer la lista tiene la desventaja de que es un proceso un poco más lento y requiere administrar intervalos de identificadores de recursos. Tiene la ventaja de que una aplicación de cliente que se vincula a varios archivos DLL de extensión MFC puede utilizar cualquier recurso proporcionado por el archivo DLL sin tener que especificar el identificador de instancia del archivo DLL. `AfxFindResourceHandle` es una API que se usa para recorrer la lista de recursos a fin de buscar una coincidencia determinada. Para ello, utiliza el nombre y el tipo de recurso, y devuelve el identificador de recurso donde se encontró por primera vez (o el valor NULL).  
  
##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Escribir una aplicación que utiliza la versión del archivo DLL  
  
### <a name="application-requirements"></a>Requisitos de la aplicación  
 Una aplicación que utiliza la versión compartida de MFC debe seguir unas reglas sencillas:  
  
-   Debe tener un `CWinApp` de objetos y cumplir las reglas estándares de una bomba de mensaje.  
  
-   Primero debe compilarse con un conjunto de marcas de compilador necesarias (ver abajo).  
  
-   Debe vincular con las bibliotecas de importación MFCxx. Al establecer los marcadores del compilador necesarios, los encabezados de MFC determinan en tiempo de vinculación biblioteca en la que la aplicación debe vincularse a.  
  
-   Para ejecutar el archivo ejecutable, MFCxx.DLL deben estar en la ruta de acceso o en el directorio del sistema de Windows.  
  
### <a name="building-with-the-development-environment"></a>Compilar con el entorno de desarrollo  
 Si usas el archivo MAKE interno con la mayoría de los valores predeterminados estándares, puede cambiar fácilmente el proyecto para compilar la versión del archivo DLL.  
  
 El siguiente paso se da por supuesto que tiene una aplicación MFC funcione correctamente vinculada con NAFXCWD. LIB (para depuración) y NAFXCW. LIB (para versión comercial) y desea convertir para que utilice la versión compartida de la biblioteca MFC. Ejecuta el entorno de Visual C++ y tiene un archivo de proyecto interno.  
  
1.  En el **proyectos** menú, haga clic en **propiedades**. En el **General** página en **valores predeterminados del proyecto**, establézcalo Microsoft Foundation Classes **utilizar MFC en un archivo DLL compartido** (MFCxx(d).dll).  
  
### <a name="building-with-nmake"></a>Compilar con NMAKE  
 Si está usando la característica de archivo MAKE externo de Visual C++, o está usando NMAKE directamente, tendrá que editar el archivo MAKE para admitir opciones del compilador y del vinculador  
  
 Marcas del compilador necesarios:  
  
 **/ / MD D_AFXDLL**  
 **/ D_AFXDLL**  
  
 Los encabezados MFC estándar necesitan este símbolo definirse:  
  
 **/MD**  
 La aplicación debe utilizar la versión del archivo DLL de la biblioteca de tiempo de ejecución de C  
  
 Todas las otras marcas del compilador siguen los valores predeterminados MFC (por ejemplo, _DEBUG para depuración).  
  
 Editar la lista del vinculador de bibliotecas. Cambio NAFXCWD. LIB para MFCxxD.LIB y cambiar NAFXCW. LIB para MFCxx.LIB. Reemplace LIBC. LIB con MSVCRT. LIB. Igual que con cualquier otra biblioteca MFC es importante que se encuentra ubicada MFCxxD.LIB **antes de** las bibliotecas en tiempo de ejecución de C.  
  
 Opcionalmente, agregar **/D_AFXDLL** a su comercial y depuración opciones del compilador de recursos (que realmente compila los recursos con **/r**). Esto hace que el ejecutable final menor compartiendo los recursos que se encuentran en los archivos DLL de MFC.  
  
 Una reconstrucción completa es necesaria una vez realizados estos cambios.  
  
### <a name="building-the-samples"></a>Compilar los ejemplos  
 La mayoría de los programas de ejemplo MFC se puede generar desde Visual C++ o desde un archivo MAKE de NMAKE compatible compartido desde la línea de comandos.  
  
 Para convertir cualquiera de estos ejemplos que se usará MFCxx.DLL, puede cargar el. MAK el archivo en Visual C++ y establecer las opciones de proyecto, como se describió anteriormente. Si usas la compilación NMAKE, puede especificar "AFXDLL = 1" en el NMAKE línea de comandos y que se compilará el ejemplo utilizando las bibliotecas compartidas de MFC.  
  
 El ejemplo de conceptos avanzados de MFC [DLLHUSK](../visual-cpp-samples.md) se genera con la versión del archivo DLL de MFC. No solo, en este ejemplo muestra cómo crear una aplicación vinculada con MFCxx.DLL, pero también muestra otras características de la opción de empaquetado de DLL de MFC, como archivos DLL de extensión de MFC se describe más adelante en esta nota técnica.  
  
### <a name="packaging-notes"></a>Notas de empaquetado  
 La versión comercial de los archivos DLL (MFCxx [U]. DLL) son redistribuibles libremente. La versión de depuración de los archivos DLL no se puede redistribuir libremente y debe utilizarse solo durante el desarrollo de la aplicación.  
  
 La DLL de depuración se proporcionan con información de depuración. Mediante el depurador de Visual C++, permite realizar el seguimiento de ejecución de la aplicación, así como el archivo DLL. Los archivos DLL de versión (MFCxx [U]. DLL) no contienen información de depuración.  
  
 Si se personalizan o volver a generar los archivos DLL, a continuación, debe llamar a ellos algo distinto de archivo "MFCxx" The MFC SRC MFCDLL. MAK describe las opciones de compilación y contiene la lógica para cambiar el nombre del archivo DLL. Cambiar el nombre de los archivos es necesario, ya que estos archivos DLL potencialmente se comparten muchas de las aplicaciones de MFC. Con su versión personalizada de la sustitución de archivos DLL de MFC están instalados en el sistema pueden interrumpir otra aplicación MFC con las DLL de MFC compartidas.  
  
 No se recomienda volver a generar los archivos DLL de MFC.  
  
##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> Cómo se implementa MFCxx.DLL  
 La siguiente sección describe cómo se implementa la DLL de MFC (MFCxx.DLL y MFCxxD.DLL). Descripción de que los detalles aquí también no son importante si todo lo que desea hacer es utilizar la DLL de MFC con la aplicación. Los detalles aquí no son esenciales para comprender cómo escribir un archivo DLL de extensión MFC, pero la descripción de esta implementación puede ayudarle a escribir su propio archivo DLL.  
  
### <a name="implementation-overview"></a>Información general de implementación  
 La DLL de MFC es realmente un caso especial de una DLL de extensión de MFC, como se describió anteriormente. Tiene un gran número de exportaciones de un gran número de clases. Hay algunos aspectos adicionales que puede hacer en la DLL de MFC que hacen que sea incluso más especial que un archivo DLL de extensión MFC normal.  
  
### <a name="win32-does-most-of-the-work"></a>Win32 realiza la mayor parte del trabajo  
 La versión de 16 bits de MFC necesita una serie de técnicas especiales incluidos los datos por aplicación en el segmento de pila, segmentos especiales creados por algún código de ensamblado de 80 x 86, contextos de excepción por proceso y otras técnicas. Win32 admite directamente por el procesamiento de datos en un archivo DLL, que es la acción que realizará la mayor parte del tiempo. En su mayor parte MFCxx.DLL es simplemente NAFXCW. LIB empaquetado en un archivo DLL. Si observa el código fuente MFC, encontrará muy pocas _AFXDLL #ifdef, dado que hay muy pocos casos especiales que deben realizarse. Los casos especiales que están hay específicamente para tratar con Win32 en Windows 3.1 (también conocida como Win32s). Win32s no no soporte por proceso DLL datos directamente de modo que la DLL de MFC debe utilizar el almacenamiento local de subprocesos (TLS) las API de Win32 para obtener los datos locales de proceso.  
  
### <a name="impact-on-library-sources-additional-files"></a>Impacto en la biblioteca de fuentes, archivos adicionales  
 El impacto de la **_AFXDLL** versión en los encabezados y orígenes de biblioteca de clase MFC normal es relativamente pequeños. Hay un archivo de la versión especial (AFXV_DLL. (H), así como un archivo de encabezado adicional (AFXDLL_. (H) incluidos en el AFXWIN principal. Encabezado de H. AFXDLL_. H encabezado incluye la **CDynLinkLibrary** clase y otros detalles de implementación de ambos **_AFXDLL** aplicaciones y archivos DLL de extensión de MFC. AFXDLLX. Encabezado de H se proporciona para la creación de archivos DLL de extensión de MFC (vea más arriba para obtener más información).  
  
 Los orígenes regulares a la biblioteca MFC en MFC SRC tienen condicional código adicional en el **_AFXDLL** #ifdef. Un archivo de origen adicionales (DLLINIT. CPP) contiene el código de inicialización de DLL adicional y otro adherencia para la versión compartida de MFC.  
  
 Para compilar la versión compartida de MFC, se proporcionan archivos adicionales. (Vea a continuación para obtener más información sobre cómo crear el archivo DLL).  
  
-   Dos. DEF (archivos) se utilizan para exportar los puntos de entrada de DLL de MFC para depuración (MFCxxD.DEF) y versión (MFCxx.DEF) del archivo DLL.  
  
-   Un archivo. Archivo RC (MFCDLL. RC) contiene todos los recursos MFC estándares y un recurso VERSIONINFO para el archivo DLL.  
  
-   UN ARCHIVO. Archivo CLW (MFCDLL. CLW) se proporciona permitir el examen de la MFC clases con ClassWizard. Nota: esta característica no está determinada a la versión DLL de MFC.  
  
### <a name="memory-management"></a>Administración de memoria  
 Una aplicación que use MFCxx.DLL utiliza un asignador de memoria común proporcionado por MSVCRTxx.DLL, el archivo DLL en tiempo de ejecución de C compartido. La aplicación, los archivos DLL de extensión MFC y así como los mismos archivos DLL de MFC utilizan este asignador de memoria compartida. Mediante el uso de un archivo DLL compartido para la asignación de memoria, los archivos DLL de MFC puede asignar memoria que más adelante se libera por la aplicación, o viceversa. Debido a la aplicación y el archivo DLL deben utilizar el mismo asignador, no debe reemplazar el C++ global `operator new` o `operator delete`. Las mismas reglas que se aplican al resto de las rutinas de asignación de memoria en tiempo de ejecución de C (como `malloc`, `realloc`, **libre**etc.).  
  
### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>Ordinales y clase __declspec (dllexport) y nombres de archivo DLL  
 No usamos el `class` **__declspec (dllexport)** la funcionalidad del compilador de C++. En su lugar, una lista de las exportaciones se incluye con los orígenes de la biblioteca de clase (MFCxx.DEF y MFCxxD.DEF). Se exportan solo estos seleccione conjunto de puntos de entrada (funciones y datos). Otros símbolos, como funciones de implementación privada de MFC o de clases, no se exportan todas las exportaciones se realizan mediante el valor ordinal sin un nombre de cadena en la tabla de nombres residentes o no residentes.  
  
 Usar `class` **__declspec (dllexport)** puede ser una alternativa viable para la creación de archivos DLL más pequeñas, pero en el caso de un archivo DLL grande como MFC, el valor predeterminado exportar mecanismo tiene la eficacia y la capacidad de límites.  
  
 ¿Qué es esto significa que todos los que le podemos empaquetar una gran cantidad de funcionalidad en la versión MFCxx.DLL que solo unos 800 KB sin poner en peligro la cantidad ejecución o cargando velocidad. MFCxx.DLL habría sido mayor de 100 KB esta técnica no se hubiera utilizado. Esto también hace posible agregar puntos de entrada adicionales al final de la. Archivo DEF para permitir el control de versiones simple sin poner en peligro la eficacia de velocidad y el tamaño de exportar por ordinal. Revisiones de la versión principal de la biblioteca de clases MFC cambiará el nombre de la biblioteca. Es decir, MFC30. DLL es la DLL redistribuible que contiene la versión 3.0 de la biblioteca de clases MFC. Una actualización de este archivo DLL, digamos, en una hipotética 3.1 de MFC, el archivo DLL se denominará MFC31. DLL en su lugar. Una vez más, si modifica el código fuente MFC para generar una versión personalizada de la DLL de MFC, use un nombre diferente (y preferiblemente uno sin "MFC" en el nombre).  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

