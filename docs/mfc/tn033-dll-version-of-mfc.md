---
title: "TN033: Versi&#243;n de DLL de MFC | Microsoft Docs"
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
  - "vc.mfc.dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "biblioteca AFXDLL"
  - "versión del archivo DLL de MFC [C++]"
  - "DLL [C++], MFC"
  - "DLL de MFC [C++], escribir extensiones DLL"
  - "TN033"
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN033: Versi&#243;n de DLL de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota se describe cómo utilizar las bibliotecas de vínculos dinámicos compartidas MFCxx.DLL y MFCxxD.DLL \(donde x es el número de versión de MFC\) con aplicaciones MFC y archivos DLL de extensión.  Para obtener más información sobre los archivos DLL estándar, vea [Utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).  
  
 Esta nota técnica se abordan tres aspectos de archivos DLL.  Los dos últimos son para los más usuarios avanzados:  
  
-   [Cómo se compila un archivo DLL de extensión de MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)  
  
-   [Cómo se compila una aplicación MFC que utiliza la versión de DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)  
  
-   [Cómo se implementan las bibliotecas de vínculos dinámicos compartidas MFC](#_mfcnotes_how_the_mfc30.dll_is_implemented)  
  
 Si está interesado en compilar un archivo DLL de MFC que se puede utilizar con las aplicaciones de no MFC \(esto se denomina un archivo DLL estándar\), hace referencia a [Nota técnica 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).  
  
## Información general de compatibilidad de MFCxx.DLL: Términos y archivos  
 **Regular DLL**: Utiliza un archivo DLL estándar para compilar un archivo DLL independiente con algunas de las clases de MFC.  Las interfaces a través del límite de App\/DLL son interfaces “c”, y la aplicación cliente no tiene que ser una aplicación MFC.  
  
 Ésta es la versión de compatibilidad de DLL compatible en MFC 1,0.  Se describe en [Nota técnica 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) y MFC avanzada de ejemplo [DLLScreenCap](../top/visual-cpp-samples.md)de los conceptos.  
  
> [!NOTE]
>  A partir de la versión 4.0 de Visual C\+\+, el término **USRDLL** está obsoleto y se ha sustituido por un archivo DLL estándar que se vincule estáticamente a MFC.  También puede compilar un archivo DLL estándar que se vincule dinámicamente a MFC.  
  
 MFC 3,0 \(y arriba\) admite los archivos DLL estándar con toda la nueva funcionalidad incluidos OLE y las clases de base de datos.  
  
 **AFXDLL**: Esto también se conoce como la versión compartida de las bibliotecas MFC.  Este es el nuevo compatibilidad de DLL agregado en MFC 2,0.  La biblioteca MFC está en varios archivos DLL \(descritos a continuación\) y una aplicación cliente o DLL enlaza dinámicamente los archivos DLL que requiere.  Las interfaces a través del límite de application\/DLL son interfaces de clase de C\+\+\/MFC.  La aplicación cliente MUST es una aplicación MFC.  Esto admite toda la funcionalidad de MFC 3,0 \(excepción: UNICODE no se admite para las clases de base de datos\).  
  
> [!NOTE]
>  A partir de la versión 4.0 de Visual C\+\+, hacen referencia a este tipo de archivo DLL como “archivo DLL de extensión”.  
  
 Esta nota utilizará MFCxx.DLL para hacer referencia a MFC completo DLL establecido, que incluye:  
  
-   Depuración: MFCxxD.DLL \(combinado\) y MFCSxxD.LIB \(estático\).  
  
-   Versión: MFCxx.DLL \(combinado\) y MFCSxx.LIB \(estático\).  
  
-   Depuración Unicode: MFCxxUD.DLL \(combinado\) y MFCSxxD.LIB \(estático\).  
  
-   Lanzamiento Unicode: MFCxxU.DLL \(combinado\) y MFCSxxU.LIB \(estático\).  
  
> [!NOTE]
>  Las bibliotecas de MFCSxx \[U\] \[d\] .LIB se utilizan junto con los archivos DLL compartidos MFC.  Estas bibliotecas contienen el código que se debe vincular estáticamente a la aplicación o a un archivo DLL.  
  
 Vínculos de una aplicación a las bibliotecas correspondientes import:  
  
-   Depuración: MFCxxD.LIB  
  
-   Versión: MFCxx.LIB  
  
-   Depuración Unicode: MFCxxUD.LIB  
  
-   Lanzamiento Unicode: MFCxxU.LIB  
  
 Una “archivo DLL de extensión MFC” es un archivo DLL compilado sobre el archivo \(o los otros archivos DLL compartidos MFC\).  Aquí la arquitectura componente de MFC alcanza con el pie en.  Si deriva una clase útil de una clase MFC, o compile otra MFC\- como kit de herramientas, puede colocarlo en un archivo DLL.  Que DLL utiliza MFCxx.DLL, al igual que la última aplicación cliente.  Esto permite clases reutilizables de hoja, clases base reutilizables, y clases reutilizables de vista\/documento.  
  
## Ventajas y desventajas  
 ¿Por qué debe utilizar la versión compartida de MFC?  
  
-   Mediante la biblioteca compartida puede dar lugar a aplicaciones más pequeñas \(una aplicación mínima que utiliza la mayor parte de la biblioteca MFC es menor que 10K\).  
  
-   La versión compartida de MFC admite el archivo DLL de extensión y DLL de MFC.  
  
-   Compilar una aplicación que utilice bibliotecas compartidas de MFC es más rápido compilar una aplicación estáticamente vinculada de MFC porque no es necesario vincular MFC.  Esto es especialmente cierto en las compilaciones de **DEBUG** donde el vinculador debe compactar la información de depuración — vincular a un archivo DLL que ya contiene la información de depuración, hay menos información de depuración a compactar dentro de la aplicación.  
  
 Por qué debe no utilizar la versión compartida de MFC:  
  
-   El envío de una aplicación que usa la biblioteca compartida requiere que envía la biblioteca de MFCxx.DLL \(y otros\) con el programa.  MFCxx.DLL es libremente redistribuible como muchos archivos DLL, pero todavía debe instalar el archivo DLL en el programa de instalación.  Además, debe enviar el MSVCRTxx.DLL, que contiene la biblioteca en tiempo de ejecución de C que utiliza el programa y los archivos DLL de MFC.  
  
##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Cómo escribir un archivo DLL de extensión de MFC  
 Un archivo DLL de extensión de MFC es clases contenedoras y funciones de un archivo DLL escritas para embellecer la funcionalidad de las clases MFC.  Un archivo DLL de extensión MFC utiliza los archivos DLL compartidos de MFC que una aplicación la utilizan de la misma manera, con algunas consideraciones adicionales:  
  
-   El proceso de compilación es similar a compilar una aplicación que utilice bibliotecas compartidas de MFC con algunos opciones adicionales del compilador y el vinculador.  
  
-   Un archivo DLL de extensión MFC no tiene `CWinApp`\- clase derivada.  
  
-   Un archivo DLL de extensión MFC debe proporcionar `DllMain`especial.  Fuentes de AppWizard una función de `DllMain` que puede modificar.  
  
-   Un archivo DLL de extensión MFC proporcionará normalmente una rutina de inicialización para crear **CDynLinkLibrary** si deseos de DLL de extensión para exportar `CRuntimeClass`es o recursos a la aplicación.  Una clase derivada de **CDynLinkLibrary** puede usar si los datos de la por\- aplicación deben mantener por el archivo DLL de extensión.  
  
 Estas consideraciones se describen con más detalle más adelante.  También debe hacer referencia a MFC avanzada de ejemplo [DLLHUSK](../top/visual-cpp-samples.md) de conceptos ya que muestra:  
  
-   Compilar una aplicación mediante las bibliotecas compartidas. \(DLLHUSK.EXE es una aplicación MFC que enlaza dinámicamente a MFC bibliotecas junto con otros archivos DLL\).  
  
-   Compilar un archivo DLL de extensión de MFC. \(Observe las marcas especiales como `_AFXEXT` que se utilizan en compilar un archivo DLL de extensión\)  
  
-   Dos ejemplos de los archivos DLL de extensión de MFC.  Uno se muestra la estructura básica de un archivo DLL de extensión MFC con exportaciones limitadas \(TESTDLL1\) y la otra muestra exportar una interfaz de clase completa \(TESTDLL2\).  
  
 La aplicación cliente y cualquier archivo DLL de extensión deben utilizar la misma versión de MFCxx.DLL.  Debe seguir la convención de MFC DLL y proporcionar una depuración y la versión de la versión comercial \(\/release\) del archivo DLL de extensión.  Esto permite que los programas cliente compilen depuración y versiones comerciales de las aplicaciones y que las vinculadas con la depuración correcta o la versión comercial de todos los archivos DLL.  
  
> [!NOTE]
>  Dado que los problemas de destrucción y exportación de nombres de C\+\+, la lista de exportación de un archivo DLL de extensión pueden ser diferentes en las versiones de depuración y de lanzamiento del mismo archivo y archivos DLL para distintas plataformas.  La versión de lanzamiento MFCxx.DLL tiene alrededor de 2000 puntos de entrada exportados; depuración MFCxxD.DLL tiene alrededor de 3000 puntos de entrada exportados.  
  
### Nota rápida en la administración de memoria  
 La sección titulada “administración de memoria,” cerca del final de esta nota técnica, describe la implementación de MFCxx.DLL con la versión compartida de MFC.  La información que necesita saber para implementar simplemente un archivo DLL de extensión se describe aquí.  
  
 MFCxx.DLL y todos los archivos DLL de extensión cargados en el espacio de direcciones de la aplicación cliente utilizarán el mismo asignador de memoria, la carga de recursos y otros estados “globales” de MFC como si estuvieran en la misma aplicación.  Esto es importante porque las bibliotecas de que el archivo DLL de MFC y los archivos DLL estándar vinculados estáticamente a MFC en MFC y los de y tienen cada DLL que asigna fuera de su propio bloque de memoria.  
  
 Si un archivo DLL de extensión asigna memoria, dicha memoria puede combinarse libremente con cualquier otro objeto aplicación\- asignado.  Además, si se bloquea una aplicación que usa las bibliotecas compartidas de MFC, la protección del sistema operativo mantendrá la integridad de cualquier otra aplicación MFC que comparte el archivo DLL.  
  
 De igual forma comparten otros estados “globales” de MFC, como el archivo ejecutable actual para cargar recursos, también entre la aplicación cliente y todos los archivos DLL así como MFCxx.DLL propio de extensión de MFC.  
  
### Compilar un archivo DLL de extensión  
 Puede utilizar AppWizard para crear un proyecto de archivo DLL de extensión de MFC, y generará automáticamente los valores adecuados del compilador y el vinculador.  Era también genera una función de `DllMain` que puede modificar.  
  
 Si está convirtiendo un proyecto existente a un archivo DLL de extensión de MFC, inicia con las reglas estándar para generar una aplicación utilizando la versión compartida de MFC, haga lo siguiente:  
  
-   Agregue **\/D\_AFXEXT** a marcadores del compilador.  En el cuadro de diálogo propiedades del proyecto, seleccione el nodo de C\/C\+\+.  Seleccione la categoría de preprocesador.  Agregue `_AFXEXT` al campo de macros de Define, separando cada uno de los elementos con puntos y coma.  
  
-   Quite el modificador del compilador **\/Gy** .  En el cuadro de diálogo propiedades del proyecto, seleccione el nodo de C\/C\+\+.  Seleccione la categoría de la generación de código.  Asegúrese de que el “Función\- nivel de permiso que vincula” la opción no está habilitado.  Así resultará más fácil exportar clases porque el vinculador no quitará funciones sin referencia.  Si se utiliza el proyecto original de compilar un archivo DLL estándar vinculado estáticamente a MFC, cambie la opción del compilador **\/MT\[d\]** a **\/MD\[d\]**.  
  
-   Compilar una biblioteca de exportación con la opción de **\/DLL** A LINK.  Se establece cuando se crea un nuevo destino, especificando la biblioteca de vínculos dinámicos de Win32 como el tipo de destino.  
  
### Cambiar los archivos de encabezado  
 El objetivo de un archivo DLL de extensión normalmente es exportar alguna funcionalidad común a una o más aplicaciones que pueden utilizar esa funcionalidad.  Esto hierve abajo a exportar clases y funciones globales que están disponibles para las aplicaciones cliente.  
  
 Para ello debe garantizar que cada una de las funciones miembro está marcada como importación o exportación según corresponda.  Esto requiere declaraciones especiales: **\_\_declspec\(dllexport\)** y **\_\_declspec\(dllimport\)**.  Cuando las clases son utilizadas por las aplicaciones cliente, desea que se declararán como **\_\_declspec\(dllimport\)**.  Cuando se está compilando el archivo DLL de extensión propio, se deben declarar como **\_\_declspec\(dllexport\)**.  Además, las funciones deben exportarse realmente, de modo que los programas cliente enlazados a ellas en tiempo de carga.  
  
 Para exportar la clase completa, utilice **AFX\_EXT\_CLASS** en la definición de clase.  Define esta macro por el marco como **\_\_declspec\(dllexport\)** cuando se define **\_AFXDLL** y `_AFXEXT` , pero definida como **\_\_declspec\(dllimport\)** cuando `_AFXEXT` no está definido.  `_AFXEXT` como se describió anteriormente, se define únicamente al compilar el archivo DLL de extensión.  Por ejemplo:  
  
```  
class AFX_EXT_CLASS CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
### No se exporta la clase completa  
 Puede que a veces desee exportar solo los miembros necesarios individuales de la clase.  Por ejemplo, si va a exportar una clase derivada de `CDialog`, quizá sólo necesite exportar el constructor y la llamada a `DoModal`.  Puede exportar a estos miembros mediante el archivo de .DEF de DLL, pero también puede utilizar **AFX\_EXT\_CLASS** casi de la misma manera en los miembros individuales que desea exportar.  
  
 Por ejemplo:  
  
```  
class CExampleDialog : public CDialog  
{  
public:  
   AFX_EXT_CLASS CExampleDialog();  
   AFX_EXT_CLASS int DoModal();  
   // rest of class definition  
   .  
   .  
   .  
};  
```  
  
 Al hacer esto, puede producirse un problema adicional porque ya no va a exportar todos los miembros de la clase.  El problema es de la manera en que funcionan las macros MFC.  Varias macros auxiliares de MFC sirven en realidad para declarar o definir miembros de datos.  Por consiguiente, estos miembros de datos también deberán exportarse de DLL.  
  
 Por ejemplo, la macro `DECLARE_DYNAMIC` se define de la manera siguiente cuando se compila un archivo DLL de extensión:  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
   public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
 La línea que empieza “ `AFX_DATA`estático” está declarando un objeto estático de la clase.  Para exportar correctamente esta clase y tener acceso a la información en tiempo de ejecución de un cliente .EXE, debe exportar este objeto estático.  Como el objeto estático se declara con el modificador `AFX_DATA`, sólo tendrá que definir `AFX_DATA` como **\_\_declspec\(dllexport\)** al compilar el archivo DLL y definirlo como **\_\_declspec\(dllimport\)** al compilar el archivo ejecutable cliente.  
  
 Tal y como se describe anteriormente, **AFX\_EXT\_CLASS** está definida de esta manera.  Sólo se necesita volver `AFX_DATA` sea igual que **AFX\_EXT\_CLASS** alrededor de la definición de clase.  
  
 Por ejemplo:  
  
```  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
class CExampleView : public CView  
{  
  DECLARE_DYNAMIC()  
  // ... class definition ...  
};  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
 MFC siempre utiliza el símbolo de `AFX_DATA` en elementos de datos que define dentro de las macros, por lo que esta técnica funcionará para todos estos escenarios.  Por ejemplo, funcionará para `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Si va a exportar toda la clase en lugar de miembros seleccionados de la clase, se exportan automáticamente los miembros de datos estáticos.  
  
 Puede utilizar la misma técnica automáticamente de exportar el operador de extracción de `CArchive` para las clases que utilizan macros de `DECLARE_SERIAL` y de `IMPLEMENT_SERIAL` .  Exporte el operador de archivo acorchetando las declaraciones de clase \(encuentran en. Archivo de h\) con el código siguiente:  
  
```  
#undef AFX_API  
#define AFX_API AFX_EXT_CLASS  
  
<your class declarations here>  
  
#undef AFX_API  
#define AFX_API  
```  
  
### Limitaciones de \_AFXEXT  
 Puede utilizar el símbolo de preprocesador**AFXEXT** de \_para archivos DLL de extensión siempre que no tenga varios niveles de archivos DLL de extensión.  Si tiene archivos DLL de extensión que puede llamar o derivar desde clases de sus propios archivos DLL de extensión, que se derivan de las clases MFC, debe utilizar su propio símbolo de preprocesador para evitar la ambigüedad.  
  
 El problema es que en Win32, debe declarar explícitamente todos los datos como **\_\_declspec\(dllexport\)** si se van a exportar desde un archivo DLL, y como **\_\_declspec\(dllimport\)** si se van a importar desde un archivo DLL.  Cuando defina `_AFXEXT`, los encabezados de MFC garantizarán que **AFX\_EXT\_CLASS** esté correctamente definido.  
  
 Cuando tenga varios niveles, un símbolo como **AFX\_EXT\_CLASS** no es suficiente, ya que un archivo DLL de extensión puede exportar clases nuevas así como importar otras clases de otro archivo DLL de extensión.  Para resolver este problema, utilice un símbolo de preprocesador especial que indica que está compilando el archivo DLL utilizándolo.  Por ejemplo, imagine dos archivos DLL de extensión, A.DLL, y B.DLL.  Cada uno de ellos exporta algunas clases de A.H y B.H, respectivamente.  B.DLL utiliza las clases de A.DLL.  Los archivos de encabezado presentarían el siguiente aspecto:  
  
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
  
 Cuando se compila A.DLL, se compila con **\/D A\_IMPL** y cuando se compila B.DLL, se compila con **\/D B\_IMPL**.  Con símbolos independientes para cada archivo DLL, CExampleB se exporta y CExampleA se importa al compilar B.DLL.  Se exporta al compilar A.DLL e importa CExampleA cuando utiliza B.DLL \(o algún otro cliente\).  
  
 Este tipo de disposición no pueden hacer al utilizar **AFX\_EXT\_CLASS** y símbolos integrados de preprocesador `_AFXEXT` .  La técnica descrita soluciona este problema de una manera que el mecanismo MFC utiliza al compilar los archivos DLL de extensión OLE, de la base de datos, y de red.  
  
### No se exporta la clase completa  
 Una vez más tendrá que tener cuidado especial cuando no se exporte toda la clase.  Debe asegurarse de que los elementos de datos necesarios creados por las macros MFC se exportan correctamente.  Esto puede ser hace redefiniendo **AFX\_DATA** a la macro de las clases concretas.  Debe hacerse siempre que no se exporte toda la clase.  
  
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
   //class definition   
   .  
   .  
   .  
};  
  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### DllMain  
 A continuación se muestra el código exacto que debe usar en el archivo de código fuente principal para el archivo DLL de extensión.  Debe aparecer después de que el estándar incluye.  Tenga en cuenta que cuando se utiliza AppWizard para crear los archivos iniciales para un archivo DLL de extensión, proporciona `DllMain` automáticamente.  
  
```  
#include "afxdllx.h"  
  
static AFX_EXTENSION_MODULE extensionDLL;  
  
extern "C" int APIENTRY   
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)  
{  
   if (dwReason == DLL_PROCESS_ATTACH)  
   {  
      // Extension DLL one-time initialization   
      if (!AfxInitExtensionModule(  
             extensionDLL, hInstance))  
         return 0;  
  
      // TODO: perform other initialization tasks here  
   }  
   else if (dwReason == DLL_PROCESS_DETACH)  
   {  
      // Extension DLL per-process termination  
      AfxTermExtensionModule(extensionDLL);  
  
          // TODO: perform other cleanup tasks here  
   }  
   return 1;   // ok  
}  
```  
  
 La llamada a `AfxInitExtensionModule` captura las tiempo de ejecución\- clases de módulos \(estructuras de`CRuntimeClass` \) así como todos los generadores de objetos \(de`COleObjectFactory` \) para el uso posterior cuando se crea el objeto de **CDynLinkLibrary** .  La llamada \(opcional\) a `AfxTermExtensionModule` ofrece a MFC a limpieza el archivo DLL de extensión cuando cada proceso desasocia \(esto ocurre cuando los resultados de procesos, o cuando se descarga el archivo DLL como resultado de una llamada de **FreeLibrary** \) del archivo DLL de extensión.  Dado que la mayoría de los archivos DLL de extensión no se cargan dinámicamente \(normalmente, se vinculan a través de las bibliotecas de importación\), la llamada a `AfxTermExtensionModule` normalmente no es necesaria.  
  
 Si la aplicación carga y libera los archivos DLL de extensión dinámicamente, asegúrese de llamar a `AfxTermExtensionModule` como se indicó anteriormente.  También asegúrese de utilizar `AfxLoadLibrary` y `AfxFreeLibrary` \(en lugar de Win32 funciona **LoadLibrary** y **FreeLibrary**\) si la aplicación utiliza varios subprocesos o si carga dinámicamente un archivo DLL de extensión.  Mediante `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y de cierre que se ejecuta cuando la extensión se carga o descarga el archivo DLL no dañe el estado global de MFC.  
  
 El archivo de encabezado AFXDLLX.H contiene definiciones especiales para las estructuras que se utilizan en archivos DLL de extensión, como la definición de `AFX_EXTENSION_MODULE` y **CDynLinkLibrary**.  
  
 *El extensionDLL* global se debe declarar como se muestra.  A diferencia de la versión de 16 bits de MFC, puede asignar memoria y llamar a las funciones de MFC durante este tiempo, ya que inicializa el archivo totalmente en el momento de llamar a `DllMain` .  
  
### Compartir recursos y clases  
 Los archivos DLL simples de extensión de MFC solamente necesitan exportar algunas funciones de bajo\- ancho banda a la aplicación cliente y nada más.  Varias DLL intensivos de la interfaz de usuario pueden desear exportar recursos y clases de C\+\+ a la aplicación cliente.  
  
 La exportación de recursos se realiza mediante una lista de recursos.  En cada aplicación es una lista vinculada de objetos de **CDynLinkLibrary** .  Al buscar un recurso, la mayoría de las implementaciones MFC estándar que cargan recursos buscan primero el módulo de recursos actual \(`AfxGetResourceHandle`\) y si no encontró el recorrido la lista de objetos de **CDynLinkLibrary** que intentan cargar el recurso solicitado.  
  
 La creación dinámica de objetos de C\+\+ con nombre de clase de c\+\+. es similar.  El mecanismo de deserialización de objetos MFC necesita todos los objetos de `CRuntimeClass` registrados para poder reconstruir creando dinámicamente el objeto C\+\+ del tipo requerido según lo que estaba almacenado antes.  
  
 Si desea que la aplicación cliente para utilizar las clases del archivo DLL de extensión que son `DECLARE_SERIAL`, deberá exportar las clases sea visible para la aplicación cliente.  Esto también hace recorrer la lista de **CDynLinkLibrary** .  
  
 En el caso de MFC avanzada del ejemplo [DLLHUSK](../top/visual-cpp-samples.md)de los conceptos, la lista tiene la siguiente apariencia:  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
               |                      |  
          TESTDLL2.DLL           TESTDLL2.DLL  
               |                      |  
          TESTDLL1.DLL           TESTDLL1.DLL  
               |                      |  
               |                      |  
            MFC90D.DLL            MFC90.DLL  
```  
  
 MFCxx.DLL suele estar al final de la lista de recursos y clases.  MFCxx.DLL incluye todos los recursos estándar de MFC, incluidas las cadenas de texto de los id. de comando estándar.  La posición de en la cola de la lista permite los archivos DLL y la aplicación cliente no tener una su propia copia de los recursos estándar de MFC, sino de basarse en los recursos compartidos en el archivo en su lugar.  
  
 La combinación de los recursos y los nombres de clase de todos los archivos DLL en el espacio de nombres de la aplicación cliente tiene la desventaja que hay que tener cuidado qué identificadores o nombres. la elección.  Puede por supuesto deshabilitar esta característica no exportando los recursos o un objeto de **CDynLinkLibrary** a la aplicación cliente.  El ejemplo [DLLHUSK](../top/visual-cpp-samples.md) administra el espacio de nombres del recurso compartido mediante varios archivos de encabezado.  Vea [Nota técnica 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) para obtener sugerencias sobre el uso de los archivos de recursos compartidos.  
  
### Inicializar un archivo DLL  
 Como se ha mencionado anteriormente, normalmente es conveniente crear un objeto de **CDynLinkLibrary** para exportar los recursos y clases a la aplicación cliente.  Necesitará proporcionar un punto de entrada exportado para inicializar un archivo DLL.  Como mínimo, es una rutina vacía que no toma ningún argumento y no devuelve nada, pero puede ser cualquier cosa que desee.  
  
 Cada aplicación cliente que desea utilizar el archivo DLL debe llamar a esta rutina de inicialización, si utiliza este enfoque.  También puede asignar este objeto de **CDynLinkLibrary** en `DllMain` justo después de llamar a `AfxInitExtensionModule`.  
  
 La rutina de inicialización debe crear un objeto de **CDynLinkLibrary** en la pila de aplicación actual, cableado hasta la información del archivo DLL de extensión.  Esto se puede hacer con el siguiente:  
  
```  
extern "C" extern void WINAPI InitXxxDLL()  
{  
   new CDynLinkLibrary(extensionDLL);  
}  
```  
  
 El nombre tiene, *InitXxxDLL* en este ejemplo, puede ser cualquier nombre que desee.  No es necesario `extern "C"`, pero hacerlo hace que la lista de exportación más fácil mantener.  
  
> [!NOTE]
>  Si utiliza el archivo DLL de extensión del archivo DLL estándar, deberá exportar esta función de inicialización.  Esta función debe llamar desde un archivo DLL estándar antes de utilizar las clases o recursos del archivo DLL de extensión.  
  
### Exportar entradas  
 La manera sencilla de exportar clases es utilizar **\_\_declspec\(dllimport\)** y **\_\_declspec\(dllexport\)** en cada clase y función global que desea en la exportación.  Esto hace que resulte más fácil, pero es menos eficaz que llamar a cada punto de entrada \(se describe más adelante\) puesto que tiene menos control sobre se exportan qué funciones y no puede exportar funciones por ordinal.  TESTDLL1 y TESTDLL2 utilizan este método para exportar sus entradas.  
  
 Un método más eficaz \(y el método utilizado por MFCxx.DLL\) es exportar cada entrada a mano llamando a cada entrada en el archivo .DEF.  Puesto que estamos exportando exportaciones selectivas de nuestro DLL \(es decir, no todo\), se debe decidir qué interfaces determinadas deseamos a la exportación.  Esto es difícil ya que debe especificar los nombres destrozados al vinculador en forma de entradas en el archivo .DEF.  No exportar las clases de C\+\+ a menos que realmente necesite tener un vínculo de token para él.  
  
 Si ha intentado exportar las clases de C\+\+ con un archivo .DEF antes, puede que quiera desarrollar una herramienta para generar esta lista automáticamente.  Esto se puede hacer mediante un proceso de dos pasos.  Vincule DLL una vez sin exportaciones, y permite que el vinculador genere un archivo de .MAP.  El archivo de .MAP se puede utilizar para generar una lista de funciones que deben exportarse, por lo que con cierto reorganizar, se puede utilizar para generar las entradas de la EXPORTACIÓN para el archivo .DEF.  La lista de exportación para MFCxx.DLL y OLE y los archivos DLL de extensión de base de datos, varios miles en gran número, generados con tal proceso \(aunque no es completamente automático y no requiere un poco de mano que adapta de tiempo en tiempo\).  
  
### CWinApp en CDynLinkLibrary  
 Un archivo DLL de extensión MFC no tiene `CWinApp`\- objeto derivado propios; en su lugar debe ejecutar `CWinApp`\- objeto derivado de la aplicación cliente.  Esto significa que la aplicación cliente es propietaria del suministro principal de mensajes, el bucle inactivo etc.  
  
 Si el archivo DLL de extensión MFC necesita mantener datos adicionales para cada aplicación, puede derivar una nueva clase de **CDynLinkLibrary** y crearlo en la rutina de InitXxxDLL describa anteriormente.  Cuando se ejecuta, el archivo DLL puede comprobar la lista de objetos **CDynLinkLibrary** de la aplicación actual para buscar el correspondiente a ese archivo DLL de extensión concreto.  
  
### Utilizar recursos en la implementación de La DLL  
 Como se mencionó anteriormente, carga predeterminada de recursos recorrerá la lista de objetos de **CDynLinkLibrary** que buscan primer EXE o DLL que tiene el recurso solicitado.  Todo el MFC API así como todo el código interno utiliza `AfxFindResourceHandle` para recorrer la lista de recursos para buscar los recursos, no importa dónde resida.  
  
 Si sólo a cargar recursos desde una ubicación específica, utilice las API `AfxGetResourceHandle` y `AfxSetResourceHandle` para guardar el identificador antiguo y establecer el nuevo identificador.  Asegúrese de restaurar el identificador de recurso antiguo antes de volver a la aplicación de cliente.  El ejemplo TESTDLL2 utiliza este enfoque para cargar explícitamente un menú.  
  
 Recorrer la lista tiene la desventaja de que es un proceso un poco más lento y requiere administrar intervalos de identificadores de recursos.  Tiene la ventaja de que una aplicación cliente que se vincula a varios archivos DLL de extensión puede usar cualquier recurso proporcionado por un archivo DLL sin tener que especificar el identificador de instancia del archivo DLL.  `AfxFindResourceHandle` es una API que se usa para recorrer la lista de recursos a fin de buscar una coincidencia determinada.  Para ello, utiliza el nombre y el tipo de recurso, y devuelve el identificador de recurso donde se encontró por primera vez \(o el valor NULL\).  
  
##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Escribiendo una aplicación Que utiliza la versión de DLL  
  
### Requisitos de la aplicación  
 Una aplicación que utiliza la versión compartida de MFC debe seguir algunas reglas simples:  
  
-   Debe tener un objeto de `CWinApp` y seguir las reglas estándar para un mensaje bombean.  
  
-   Debe compilarse con un conjunto de indicadores necesarios del compilador \(vea a continuación\).  
  
-   Debe vincular con las bibliotecas de importación MFCxx.  Estableciendo el compilador necesario marcadores, los encabezados de MFC determina en tiempo de vínculo con el que la biblioteca la aplicación debe vincularse.  
  
-   Para ejecutar el archivo ejecutable, MFCxx.DLL debe estar en la ruta de acceso o en el directorio system de Windows.  
  
### La compilación mediante el entorno de desarrollo  
 Si está utilizando el archivo MAKE interno con la mayoría de los valores predeterminados estándar, puede cambiar fácilmente el proyecto para compilar la versión de DLL.  
  
 El paso siguiente supone que tiene una aplicación MFC correctamente que funciona vinculada con NAFXCWD.LIB \(para depuración\) y NAFXCW.LIB \(para la comercial\) y desea convertirlo para utilizar la versión compartida de la biblioteca MFC.  Ejecuta el entorno de Visual C\+\+ y tiene un archivo de proyecto interno.  
  
1.  En el menú de **Proyectos** , haga clic en **Propiedades**.  En la página de **General** en **Valores predeterminados del proyecto**, establezca Microsoft Foundation Classes a **Utilizar MFC en un archivo DLL compartido** \(MFCxx \(d\) .dll\).  
  
### La compilación mediante NMAKE  
 Si utiliza la característica externa de archivos MAKE de Visual C\+\+, o utiliza NMAKE directamente, tendrá que modificar el archivo MAKE para admitir opciones del compilador y el vinculador  
  
 Indicadores necesarios del compilador:  
  
 **\/D\_AFXDLL \/MD**  
 **\/D\_AFXDLL**  
  
 Los encabezados estándar de MFC necesitan este símbolo definir:  
  
 **\/MD**  
 La aplicación debe utilizar la versión de DLL de la biblioteca en tiempo de ejecución de C  
  
 El resto de los indicadores de compilador siguen los valores predeterminados de MFC \(por ejemplo, \_DEBUG para depuración\).  
  
 Modifique la lista del vinculador de bibliotecas.  Cambie NAFXCWD.LIB a MFCxxD.LIB y cambie NAFXCW.LIB a MFCxx.LIB.  Reemplace LIBC.LIB con MSVCRT.LIB.  Como con cualquier otra biblioteca MFC es importante que MFCxxD.LIB es **before** coloca las bibliotecas en tiempo de ejecución de C.  
  
 Agregue **\/D\_AFXDLL** a la versión de lanzamiento y depuración opcionalmente las opciones del compilador de recursos \(la que compila realmente a recursos con **\/R**\).  Esto crea el menor ejecutable final compartiendo los recursos que se encuentran en los archivos DLL de MFC.  
  
 Se requiere un completo recompila después de que se realicen estos cambios.  
  
### Compilar los ejemplos  
 La mayoría de los programas de ejemplo de MFC se pueden compilar de Visual C\+\+ o un FILE MAKE compartido de NMAKE\- compatible de la línea de comandos.  
  
 Para convertir estos ejemplos para utilizar MFCxx.DLL, puede cargar el archivo de .MAK en Visual C\+\+ y establecer las opciones de proyecto como se ha descrito anteriormente.  Si está utilizando la generación de NMAKE, puede especificar “AFXDLL\=1” en la línea de comandos de NMAKE y que compile el ejemplo mediante las bibliotecas compartidas de MFC.  
  
 MFC avanzada de los conceptos que el ejemplo [DLLHUSK](../top/visual-cpp-samples.md) en la versión de DLL de MFC.  Este ejemplo no solo muestra cómo compilar una aplicación vinculada con MFCxx.DLL, pero también muestra otras características DLL de MFC que empaqueta la opción como archivos DLL de extensión de MFC que se describen más adelante en esta nota técnica.  
  
### Notas del paquete  
 La versión comercial de archivos DLL \(MFCxx \[U\] .DLL\) es libremente redistribuible.  La versión de depuración de archivos DLL no es libremente redistribuible y sólo se utiliza durante el desarrollo de la aplicación.  
  
 Los archivos DLL de depuración se proporcionan información de depuración.  Mediante el depurador de Visual C\+\+, puede seguir paso a paso la ejecución de la aplicación así como DLL.  Los archivos DLL release \(MFCxx \[U\] .DLL\) no contienen información de depuración.  
  
 Si personaliza o recompilar los archivos DLL, debe llamar que algo distinto del archivo MFCDLL.MAK de “MFCxx” MFC SRC describe opciones de compilación y que contiene la lógica para cambiar el nombre del archivo DLL.  Cambiar el nombre de archivos es necesaria, ya que estos archivos DLL potencialmente compartan numerosas aplicaciones MFC.  Obtiene la versión personalizada de los archivos DLL de MFC reemplace los instalados en el sistema puede interrumpir otra aplicación MFC mediante los archivos DLL compartidos de MFC.  
  
 Recompilar los archivos DLL de MFC no se recomienda.  
  
##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> Cómo se implementa el archivo  
 La sección siguiente se describe cómo se implementa el archivo DLL de MFC \(MFCxx.DLL y MFCxxD.DLL\).  Si comprende los detalles aquí no también son importantes si todo lo que desea hacer es utilizar el archivo DLL de MFC con la aplicación.  Los detalles aquí no son esenciales para entender cómo escribir un archivo DLL de extensión de MFC, pero la comprensión de esta implementación puede ayudarle a escribir dispone de DLL.  
  
### Información general de implementación  
 DLL de MFC es realmente un caso especial de un archivo DLL de extensión de MFC como se ha descrito anteriormente.  Tiene un gran número de exportaciones para un gran número de clases.  Hay algunos aspectos adicionales que hace en MFC DLL que lo crean aún más especial que un archivo DLL de extensión de archivo.  
  
### Win32 Admite la mayoría del trabajo  
 La versión de 16 bits de MFC para varias técnicas especiales incluidos los datos de la por\- aplicación en el segmento de pila, los segmentos especiales creados por código de ensamblado algún 80x86, contextos de excepción de por\- proceso, y otras técnicas.  Win32 admite directamente los datos de por\- proceso en un archivo DLL, que es deseable la mayoría de los casos.  En general MFCxx.DLL es simplemente NAFXCW.LIB empaquetado en un archivo DLL.  Si examina el código fuente de MFC, encontrará muy poco el \_AFXDLL \#ifdef, ya que hay muy pocos casos especiales que deben crearse.  Los casos especiales que están allí son específicamente tratar de Win32 en Windows 3.1 \(si no conocido como Win32s\).  Win32s no admite los datos del archivo DLL de por\- proceso directamente por lo que MFC DLL debe utilizar las API Win32 de \(TLS\) de almacenamiento local de subprocesos para obtener datos locales de proceso.  
  
### Impacto en los orígenes de la biblioteca, archivos adicionales  
 El impacto de la versión de **\_AFXDLL** en los orígenes y los encabezados normales de la biblioteca de clases de MFC es relativamente poco relevantes.  Hay un archivo de la versión de especial \(AFXV\_DLL.H\) así como un archivo de encabezado adicional \(AFXDLL\_.H\) incluido en el encabezado principal de AFXWIN.H.  El encabezado de AFXDLL\_.H incluye la clase de **CDynLinkLibrary** y otros detalles de la implementación de aplicaciones de **\_AFXDLL** y los archivos DLL de extensión de MFC.  El encabezado de AFXDLLX.H se proporciona para compilar archivos DLL de extensión MFC \(vea más arriba para obtener detalles\).  
  
 Los orígenes regulares a la biblioteca MFC en MFC SRC tienen código condicional adicional en \#ifdef de **\_AFXDLL** .  Un archivo de código fuente adicional \(DLLINIT.CPP\) contiene el código de inicialización del archivo DLL y el otro pegamento para la versión compartida de MFC.  
  
 Para compilar la versión compartida de MFC, los archivos adicionales se proporcionan. \(Vea a continuación para obtener información sobre cómo compilar el archivo DLL.  
  
-   Dos archivos .DEF se utilizan para exportar los puntos de entrada de archivo DLL de MFC para depuración \(MFCxxD.DEF\) y liberan las versiones \(MFCxx.DEF\) de DLL.  
  
-   Un archivo .RC \(MFCDLL.RC\) contiene todos los recursos estándar de MFC y un recurso de VERSIONINFO para DLL.  
  
-   Un archivo de .CLW \(MFCDLL.CLW\) se proporciona para permitir el examen de las clases MFC mediante ClassWizard.  Nota: esta característica no está determinada por la versión de DLL de MFC.  
  
### Administración de la memoria  
 Una aplicación mediante MFCxx.DLL utiliza un asignador común proporcionado por MSVCRTxx.DLL, el C runtime archivo DLL compartido de la memoria.  La aplicación, los archivos DLL de extensión, y así como los archivos DLL de MFC utiliza este asignador de memoria compartida.  Con DLL compartido para la asignación de memoria, los archivos DLL de MFC pueden asignar memoria que se liberó más adelante con la aplicación o viceversa.  Dado que la aplicación y DLL deben utilizar el mismo asignador, no debe invalidar C\+\+ `operator new` global o `operator delete`.  Las mismas reglas se aplican al resto de las rutinas de asignación de memoria en tiempo de ejecución de C \(como `malloc`, `realloc`, **free**, etc.\).  
  
### Ordinales y \_\_declspec de la clase \(dllexport\) y los nombres de archivo DLL  
 No se usa la funcionalidad de `class`**\_\_declspec\(dllexport\)** del compilador de C\+\+.  En su lugar, una lista de exportaciones se incluye con los orígenes de la biblioteca de clases \(MFCxx.DEF y MFCxxD.DEF\).  Sólo se exportan estos conjunto seleccione puntos de entrada \(las funciones y los datos\).  Otros símbolos, como funciones o clases privadas de implementación de MFC, no son Todas exportado que las exportaciones son realizadas por ordinal sin un nombre de cadena en el residente o la tabla no residente de nombre.  
  
 Mediante `class` **\_\_declspec\(dllexport\)** puede ser una alternativa viable para compilar archivos DLL menores, pero en el caso de DLL grande como MFC, el mecanismo que exporta predeterminado tiene límites de la eficacia y la capacidad.  
  
 Esto todo el significa que podemos empaquetar una gran cantidad de funcionalidad del lanzamiento MFCxx.DLL que sólo aproximadamente 800 KB sin comprometer de muchos ejecución o cargar velocidad.  MFCxx.DLL habría kb mayor esta técnica no se ha utilizado.  Esto también permite agregar puntos de entrada adicional al final del archivo .DEF para permitir versión sencilla sin comprometer la eficacia de la velocidad y el tamaño para exportar por ordinal.  Las revisiones importantes de la versión de la biblioteca de clases de MFC cambiará el nombre de biblioteca.  Es decir, MF C30 .DLL es un archivo DLL redistribuible que contiene la versión 3.0 de la biblioteca de clases de MFC.  Una actualización de esta DLL, por ejemplo, en MFC hipotético 3,1, la DLL se denominaría MF C31 .DLL en su lugar.  Si modifica el código fuente de MFC para generar una versión personalizada del archivo DLL de MFC, utilice una vez más un nombre diferente \(y preferiblemente uno sin “MFC” en el nombre\).  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)