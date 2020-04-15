---
title: 'TN033: Versión de DLL de MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: ad4cb883cfe7e397cf599d659afb02b23501dc5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370312"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: Versión de DLL de MFC

Esta nota describe cómo puede usar las bibliotecas de vínculos dinámicos compartidos MFCxx.DLL y MFCxxD.DLL (donde x es el número de versión de MFC) con aplicaciones MFC y archivos DLL de extensión MFC. Para obtener más información acerca de los archivos DLL de MFC normales, vea [Uso de MFC como parte de un archivo DLL.](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

Esta nota técnica abarca tres aspectos de los archivos DLL. Los dos últimos son para los usuarios más avanzados:

- [Cómo crear un archivo DLL de extensión MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Cómo se compila una aplicación MFC que usa la versión DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Cómo se implementan las bibliotecas de vínculos dinámicos compartidos de MFC](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Si está interesado en crear un archivo DLL con MFC que se puede utilizar con aplicaciones que no son MFC (esto se denomina DLL de MFC normal), consulte [la Nota técnica 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Descripción general de la compatibilidad con MFCxx.DLL: Terminología y archivos

**DLL de MFC normal:** se usa un archivo DLL de MFC normal para crear un archivo DLL independiente mediante algunas de las clases MFC. Las interfaces a través del límite de App/DLL son interfaces "C" y la aplicación cliente no tiene que ser una aplicación MFC.

Esta es la versión de compatibilidad con DLL compatible con MFC 1.0. Se describe en [la Nota técnica 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) y en el ejemplo [DLLScreenCap](../overview/visual-cpp-samples.md)de conceptos avanzados de MFC.

> [!NOTE]
> A partir de Visual C++ versión 4.0, el término **USRDLL** está obsoleto y se ha reemplazado por un archivo DLL de MFC normal que se vincula estáticamente a MFC. También puede crear un archivo DLL de MFC normal que se vincula dinámicamente a MFC.

MFC 3.0 (y superior) admite archivos DLL de MFC normales con toda la nueva funcionalidad, incluidas las clases OLE y Database.

**AFXDLL**: Esto también se conoce como la versión compartida de las bibliotecas MFC. Esta es la nueva compatibilidad con DLL agregada en MFC 2.0. La propia biblioteca MFC se encuentra en un número de archivos DLL (que se describen a continuación) y una aplicación cliente o DLL vincula dinámicamente los archivos DLL que requiere. Las interfaces a través del límite de aplicación/DLL son interfaces de clase C++/MFC. La aplicación cliente DEBE ser una aplicación MFC. Esto admite toda la funcionalidad de MFC 3.0 (excepción: UNICODE no se admite para las clases de base de datos).

> [!NOTE]
> A partir de Visual C++ versión 4.0, este tipo de DLL se conoce como un "DLL de extensión."

Esta nota utilizará MFCxx.DLL para hacer referencia a todo el conjunto de DLL de MFC, que incluye:

- Depurar: MFCxxD.DLL (combinado) y MFCSxxD.LIB (estático).

- Versión: MFCxx.DLL (combinado) y MFCSxx.LIB (estático).

- Depuración Unicode: MFCxxUD.DLL (combinado) y MFCSxxD.LIB (estático).

- Versión Unicode: MFCxxU.DLL (combinado) y MFCSxxU.LIB (estático).

> [!NOTE]
> El MFCSxx[U][D]. Las bibliotecas LIB se utilizan junto con los archivos DLL compartidos de MFC. Estas bibliotecas contienen código que debe vincularse estáticamente a la aplicación o DLL.

Una aplicación enlaza a las bibliotecas de importación correspondientes:

- Depurar: MFCxxD.LIB

- Lanzamiento: MFCxx.LIB

- Depuración Unicode: MFCxxUD.LIB

- Versión Unicode: MFCxxU.LIB

Un "DLL de extensión MFC" es un archivo DLL basado en MFCxx.DLL (y/o los otros archivos DLL compartidos de MFC). Aquí se activa la arquitectura de componentes MFC. Si deriva una clase útil de una clase MFC o compila otro kit de herramientas similar a MFC, puede colocarlo en un archivo DLL. Ese archivo DLL utiliza MFCxx.DLL, al igual que la aplicación cliente definitiva. Esto permite clases hoja reutilizables, clases base reutilizables y clases de vista/documento reutilizables.

## <a name="pros-and-cons"></a>Pros y Contras

¿Por qué debería usar la versión compartida de MFC

- El uso de la biblioteca compartida puede dar lugar a aplicaciones más pequeñas (una aplicación mínima que usa la mayor parte de la biblioteca MFC es inferior a 10K).

- La versión compartida de MFC admite archivos DLL de extensión MFC y archivos DLL de MFC normales.

- Crear una aplicación que usa las bibliotecas MFC compartidas es más rápido que crear una aplicación MFC vinculada estáticamente porque no es necesario vincular MFC sí mismo. Esto es especialmente cierto en las compilaciones **DEBUG** donde el vinculador debe compactar la información de depuración: mediante la vinculación con un archivo DLL que ya contiene la información de depuración, hay menos información de depuración para compactar dentro de la aplicación.

¿Por qué no debe utilizar la versión compartida de MFC:

- El envío de una aplicación que utiliza la biblioteca compartida requiere que envíe la biblioteca MFCxx.DLL (y otros) con el programa. MFCxx.DLL es libremente redistribuible como muchos archivos DLL, pero todavía debe instalar el archivo DLL en el programa SETUP. Además, debe enviar el archivo MSVCRTxx.DLL, que contiene la biblioteca en tiempo de ejecución de C que utiliza el programa y los propios archivos DLL de MFC.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Cómo escribir un archivo DLL de extensión MFC

Un archivo DLL de extensión de MFC es un archivo DLL que contiene clases y funciones escritas para embellecer la funcionalidad de las clases MFC. Un archivo DLL de extensión MFC utiliza los archivos DLL de MFC compartidos de la misma manera que una aplicación lo utiliza, con algunas consideraciones adicionales:

- El proceso de compilación es similar a la creación de una aplicación que usa las bibliotecas MFC compartidas con algunas opciones adicionales del compilador y del vinculador.

- Un archivo DLL de `CWinApp`extensión MFC no tiene una clase derivada.

- Un archivo DLL de `DllMain`extensión MFC debe proporcionar un archivo . AppWizard proporciona `DllMain` una función que puede modificar.

- Un archivo DLL de extensión de MFC `CDynLinkLibrary` normalmente proporcionará una `CRuntimeClass`rutina de inicialización para crear un si el archivo DLL de extensión MFC desea exportar es o recursos a la aplicación. Se puede usar `CDynLinkLibrary` una clase derivada de si el archivo DLL de extensión MFC debe mantener los datos por aplicación.

Estas consideraciones se describen con más detalle a continuación. También debe consultar el ejemplo [DLLHUSK](../overview/visual-cpp-samples.md) de conceptos avanzados de MFC, ya que ilustra:

- Creación de una aplicación mediante las bibliotecas compartidas. (DLLHUSK. EXE es una aplicación MFC que se vincula dinámicamente a las bibliotecas MFC, así como a otros archivos DLL.)

- Creación de un archivo DLL de extensión MFC. (Tenga en cuenta `_AFXEXT` las marcas especiales como las que se utilizan en la creación de un archivo DLL de extensión MFC)

- Dos ejemplos de archivos DLL de extensión MFC. Uno muestra la estructura básica de un archivo DLL de extensión MFC con exportaciones limitadas (TESTDLL1) y el otro muestra la exportación de una interfaz de clase completa (TESTDLL2).

Tanto la aplicación cliente como los archivos DLL de extensión MFC deben usar la misma versión de MFCxx.DLL. Debe seguir la convención de ARCHIVO DLL de MFC y proporcionar una versión de depuración y comercial (/release) de la DLL de extensión MFC. Esto permite que los programas cliente crear versiones de depuración y comerciales de sus aplicaciones y vincularlas con la versión de depuración o comercial adecuada de todos los archivos DLL.

> [!NOTE]
> Dado que c++ nombres de manda y problemas de exportación, la lista de exportación de un archivo DLL de extensión MFC puede ser diferente entre las versiones de depuración y comercial del mismo archivo DLL y DLL para diferentes plataformas. El archivo MFCxx.DLL minorista tiene alrededor de 2000 puntos de entrada exportados; el debug MFCxxD.DLL tiene alrededor de 3000 puntos de entrada exportados.

### <a name="quick-note-on-memory-management"></a>Nota rápida sobre la gestión de la memoria

La sección titulada "Administración de memoria", cerca del final de esta nota técnica, describe la implementación de MFCxx.DLL con la versión compartida de MFC. La información que necesita saber para implementar solo un archivo DLL de extensión MFC se describe aquí.

MFCxx.DLL y todos los archivos DLL de extensión MFC cargados en el espacio de direcciones de una aplicación cliente usarán el mismo asignador de memoria, carga de recursos y otros estados "globales" de MFC como si estuvieran en la misma aplicación. Esto es significativo porque las bibliotecas DLL que no son MFC y los archivos DLL de MFC normales que se vinculan estáticamente a MFC hacen exactamente lo contrario y tienen cada DLL asignando fuera de su propio grupo de memoria.

Si un archivo DLL de extensión MFC asigna memoria, esa memoria puede mezclarse libremente con cualquier otro objeto asignado a la aplicación. Además, si una aplicación que usa las bibliotecas MFC compartidas se bloquea, la protección del sistema operativo mantendrá la integridad de cualquier otra aplicación MFC que comparta el archivo DLL.

De forma similar, otros estados MFC "globales", como el archivo ejecutable actual desde el que cargar recursos, también se comparten entre la aplicación cliente y todos los archivos DLL de extensión MFC, así como el propio archivo MFCxx.DLL.

### <a name="building-an-mfc-extension-dll"></a>Creación de un archivo DLL de extensión MFC

Puede usar AppWizard para crear un proyecto DLL de extensión MFC y generará automáticamente la configuración adecuada del compilador y del vinculador. También se generó una `DllMain` función que se puede modificar.

Si está convirtiendo un proyecto existente en un archivo DLL de extensión MFC, comience con las reglas estándar para compilar una aplicación con la versión compartida de MFC y, a continuación, haga lo siguiente:

- Agregue **/D_AFXEXT** a los indicadores del compilador. En el cuadro de diálogo Propiedades del proyecto, seleccione el nodo C/C+++. A continuación, seleccione la categoría Preprocesador. Agregue `_AFXEXT` al campo Definir macros, separando cada uno de los elementos con punto y coma.

- Quite el modificador del compilador **/Gy.** En el cuadro de diálogo Propiedades del proyecto, seleccione el nodo C/C+++. A continuación, seleccione la categoría Generación de código. Asegúrese de que la opción "Habilitar vinculación de nivel de función" no esté habilitada. Esto facilitará la exportación de clases porque el vinculador no quitará las funciones sin referencia. Si el proyecto original se utiliza para compilar un archivo DLL de MFC normal vinculado estáticamente a MFC, cambie la opción del compilador **/MT[d]** a **/MD[d]**.

- Cree una biblioteca de exportación con la opción **/DLL** en LINK. Esto se establecerá cuando cree un nuevo destino, especificando Win32 Dynamic-Link Library como el tipo de destino.

### <a name="changing-your-header-files"></a>Cambio de los archivos de encabezado

El objetivo de un archivo DLL de extensión MFC suele ser exportar alguna funcionalidad común a una o varias aplicaciones que pueden usar esa funcionalidad. Esto se reduce a la exportación de clases y funciones globales que están disponibles para las aplicaciones cliente.

Para ello, debe asegurarse de que cada una de las funciones miembro se marque como importación o exportación según corresponda. Esto requiere declaraciones `__declspec(dllexport)` especiales: y `__declspec(dllimport)`. Cuando las clases las utilizan las aplicaciones cliente, `__declspec(dllimport)`desea que se declaren como . Cuando se compila el propio archivo DLL de `__declspec(dllexport)`extensión MFC, se deben declarar como . Además, las funciones deben exportarse realmente, de modo que los programas cliente se enlacen a ellas en tiempo de carga.

Para exportar toda la `AFX_EXT_CLASS` clase, utilice en la definición de clase. Esta macro se define `__declspec(dllexport)` por `_AFXDLL` `_AFXEXT` el marco de `__declspec(dllimport)` trabajo `_AFXEXT` como cuándo y se define, pero se define como cuando no está definido. `_AFXEXT`como se ha descrito anteriormente, solo se define al compilar el archivo DLL de extensión MFC. Por ejemplo:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>No exportar toda la clase

A veces es posible que desee exportar solo a los miembros necesarios individuales de su clase. Por ejemplo, si va `CDialog`a exportar una clase derivada, es posible `DoModal` que solo necesite exportar el constructor y la llamada. Puede exportar estos miembros mediante el archivo DLL. DEF, pero también puede `AFX_EXT_CLASS` utilizar de la misma manera en los miembros individuales que necesita exportar.

Por ejemplo:

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

Al hacerlo, puede encontrarse con un problema adicional porque ya no está exportando todos los miembros de la clase. El problema está en la forma en que funcionan las macros MFC. Varias de las macros auxiliares de MFC realmente declaran o definen miembros de datos. Por lo tanto, estos miembros de datos también tendrán que exportarse desde el archivo DLL.

Por ejemplo, la macro DECLARE_DYNAMIC se define de la siguiente manera al compilar un archivo DLL de extensión MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

La línea que comienza `AFX_DATA`"static" está declarando un objeto estático dentro de la clase. Para exportar esta clase correctamente y tener acceso a la información de tiempo de ejecución desde un cliente. EXE, debe exportar este objeto estático. Dado que el objeto estático `AFX_DATA`se declara con `AFX_DATA` el `__declspec(dllexport)` modificador , solo debe `__declspec(dllimport)` definir que sea al compilar el archivo DLL y definirlo como al compilar el ejecutable de cliente.

Como se ha `AFX_EXT_CLASS` explicado anteriormente, ya está definido de esta manera. Solo tiene que volver `AFX_DATA` a definir `AFX_EXT_CLASS` para que sea el mismo que en torno a la definición de clase.

Por ejemplo:

```cpp
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

MFC siempre `AFX_DATA` usa el símbolo en los elementos de datos que define dentro de sus macros, por lo que esta técnica funcionará para todos estos escenarios. Por ejemplo, funcionará para DECLARE_MESSAGE_MAP.

> [!NOTE]
> Si exporta toda la clase en lugar de los miembros seleccionados de la clase, los miembros de datos estáticos se exportan automáticamente.

Puede utilizar la misma técnica `CArchive` para exportar automáticamente el operador de extracción para las clases que utilizan las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. Exporte el operador de archivado entre corchetes las declaraciones de clase (ubicadas en el archivo . H) con el siguiente código:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Limitaciones de _AFXEXT

Puede usar el símbolo de preprocesador _**AFXEXT** para los archivos DLL de extensión MFC, siempre y cuando no tenga varias capas de archivos DLL de extensión MFC. Si tiene archivos DLL de extensión MFC que llaman o derivan de clases en sus propios archivos DLL de extensión MFC, que a continuación derivan de las clases MFC, debe usar su propio símbolo de preprocesador para evitar la ambiguedad.

El problema es que en Win32, debe `__declspec(dllexport)` declarar explícitamente los datos como `__declspec(dllimport)` si se va a exportar desde un archivo DLL y si se va a importar desde un archivo DLL. Al definir `_AFXEXT`, los encabezados `AFX_EXT_CLASS` MFC se aseguran de que se define correctamente.

Cuando tiene varias capas, un `AFX_EXT_CLASS` símbolo como no es suficiente, ya que un archivo DLL de extensión MFC puede estar exportando nuevas clases, así como la importación de otras clases desde otro archivo DLL de extensión MFC. Para tratar este problema, utilice un símbolo de preprocesador especial que indique que está creando el propio archivo DLL en comparación con el uso del archivo DLL. Por ejemplo, imagine dos archivos DLL de extensión MFC, A.DLL y B.DLL. Cada una exporta algunas clases en A.H y B.H, respectivamente. B.DLL utiliza las clases de A.DLL. Los archivos de encabezado se verían algo como esto:

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

Cuando se compila A.DLL, se compila con **/DA_IMPL** y cuando se compila B.DLL, se compila con **/DB_IMPL**. Mediante el uso de símbolos independientes para cada DLL, CExampleB se exporta y CExampleA se importa al compilar B.DLL. CExampleA se exporta al compilar A.DLL y se importa cuando se usa en B.DLL (o algún otro cliente).

Este tipo de capas no se puede `AFX_EXT_CLASS` realizar `_AFXEXT` cuando se utilizan los símbolos integrados y del preprocesador. La técnica descrita anteriormente resuelve este problema de una manera no diferente del mecanismo que usa MFC al compilar sus archivos DLL de extensión OLE, Database y Network MFC.

### <a name="not-exporting-the-entire-class"></a>No exportar toda la clase

Una vez más, tendrá que tener especial cuidado cuando no está exportando una clase completa. Debe asegurarse de que los elementos de datos necesarios creados por las macros MFC se exportan correctamente. Esto se puede hacer redefiniendo `AFX_DATA` la macro de la clase específica. Esto debe hacerse en cualquier momento que no esté exportando toda la clase.

Por ejemplo:

```cpp
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
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

A continuación se muestra el código exacto que debe colocar en el archivo de origen principal para el archivo DLL de extensión MFC. Debe venir después de que el estándar incluye. Tenga en cuenta que cuando se usa AppWizard para crear `DllMain` archivos de inicio para un archivo DLL de extensión MFC, proporciona un para usted.

```cpp
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

La llamada `AfxInitExtensionModule` a capturar los módulos runtime-classes (`CRuntimeClass` structures) así como sus fábricas de objetos (`COleObjectFactory` objetos) para su uso más adelante cuando se crea el `CDynLinkLibrary` objeto. La llamada (opcional) para permitir que `AfxTermExtensionModule` MFC para limpiar el archivo DLL de extensión MFC cuando cada proceso se desasocia (lo que ocurre cuando se cierra el proceso, o cuando se descarga el archivo DLL como resultado de una `FreeLibrary` llamada) desde el archivo DLL de extensión MFC. Puesto que la mayoría de los archivos DLL de extensión MFC no se cargan `AfxTermExtensionModule` dinámicamente (normalmente, están vinculados a través de sus bibliotecas de importación), la llamada a normalmente no es necesaria.

Si la aplicación carga y libera los archivos DLL de `AfxTermExtensionModule` extensión MFC dinámicamente, asegúrese de llamar como se muestra anteriormente. Asegúrese también `AfxLoadLibrary` de `AfxFreeLibrary` usar y (en `LoadLibrary` `FreeLibrary`lugar de funciones Win32 y ) si la aplicación usa varios subprocesos o si carga dinámicamente un archivo DLL de extensión MFC. Usar `AfxLoadLibrary` `AfxFreeLibrary` y asegura que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión MFC no daña el estado global de MFC.

El archivo de encabezado AFXDLLX. H contiene definiciones especiales para las estructuras utilizadas en `AFX_EXTENSION_MODULE` los `CDynLinkLibrary`archivos DLL de extensión MFC, como la definición para y .

El *extensionDLL* global debe declararse como se muestra. A diferencia de la versión de 16 bits de MFC, puede asignar memoria y llamar a funciones `DllMain` MFC durante este tiempo, ya que el archivo MFCxx.DLL se inicializa completamente en el momento en que se llama a la.

### <a name="sharing-resources-and-classes"></a>Compartir recursos y clases

Los archivos DLL de extensión MFC simples solo necesitan exportar algunas funciones de ancho de banda bajo a la aplicación cliente y nada más. Es posible que desee exportar recursos y clases C++ a la aplicación cliente.

La exportación de recursos se realiza mediante una lista de recursos. En cada aplicación hay una lista `CDynLinkLibrary` de objetos vinculada por separado. Al buscar un recurso, la mayoría de las implementaciones estándar de`AfxGetResourceHandle`MFC que cargan recursos `CDynLinkLibrary` examinan primero el módulo de recursos actual ( ) y, si no se encuentra, recorren la lista de objetos que intentan cargar el recurso solicitado.

La creación dinámica de objetos C++ con un nombre de clase C++ es similar. El mecanismo de deserialización de `CRuntimeClass` objetos MFC debe tener todos los objetos registrados para que pueda reconstruirse creando dinámicamente c++ objeto del tipo necesario en función de lo que se almacenó anteriormente.

Si desea que la aplicación cliente use clases `DECLARE_SERIAL`en el archivo DLL de extensión MFC que son , a continuación, tendrá que exportar las clases para que sea visible para la aplicación cliente. Esto también se hace `CDynLinkLibrary` caminando por la lista.

En el caso del ejemplo [DLLHUSK](../overview/visual-cpp-samples.md)de Conceptos avanzados de MFC , la lista tiene un aspecto similar al siguiente:

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

El archivo MFCxx.DLL suele ser el último en la lista de recursos y clases. MFCxx.DLL incluye todos los recursos estándar de MFC, incluidas las cadenas de solicitud para todos los atributos de comando estándar. Colocarlo en la cola de la lista permite que los archivos DLL y la propia aplicación cliente no tengan una copia propia de los recursos estándar de MFC, sino que se basen en los recursos compartidos en el archivo MFCxx.DLL en su lugar.

La combinación de los recursos y los nombres de clase de todos los archivos DLL en el espacio de nombres de la aplicación cliente tiene la desventaja de que debe tener cuidado con los identificadores o nombres que elija. Por supuesto, puede deshabilitar esta característica si no `CDynLinkLibrary` exporta los recursos o un objeto a la aplicación cliente. El ejemplo [DLLHUSK](../overview/visual-cpp-samples.md) administra el espacio de nombres de recursos compartidos mediante varios archivos de encabezado. Consulte [la Nota técnica 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) para obtener más consejos sobre el uso de archivos de recursos compartidos.

### <a name="initializing-the-dll"></a>Inicializar el archivo DLL

Como se mencionó anteriormente, `CDynLinkLibrary` normalmente querrá crear un objeto para exportar los recursos y clases a la aplicación cliente. Deberá proporcionar un punto de entrada exportado para inicializar el archivo DLL. Como mínimo, esta es una rutina nula que no toma argumentos y no devuelve nada, pero puede ser cualquier cosa que te guste.

Cada aplicación cliente que desea usar el archivo DLL debe llamar a esta rutina de inicialización, si usa este enfoque. También puede asignar `CDynLinkLibrary` este `DllMain` objeto en `AfxInitExtensionModule`su justo después de llamar a .

La rutina de `CDynLinkLibrary` inicialización debe crear un objeto en el montón de la aplicación actual, conectado a la información DLL de extensión MFC. Esto se puede hacer con lo siguiente:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

El nombre de rutina, *InitXxxDLL* en este ejemplo, puede ser cualquier cosa que desee. No es necesario que sea **extern "C"**, pero al hacerlo hace que la lista de exportación sea más fácil de mantener.

> [!NOTE]
> Si utiliza el archivo DLL de extensión MFC desde un archivo DLL de MFC normal, debe exportar esta función de inicialización. Esta función debe llamarse desde el archivo DLL de MFC normal antes de usar cualquier clase o recursos DLL de extensión MFC.

### <a name="exporting-entries"></a>Exportación de entradas

La forma sencilla de exportar `__declspec(dllimport)` sus `__declspec(dllexport)` clases es usar y en cada clase y función global que desee exportar. Esto hace que sea mucho más fácil, pero es menos eficaz que nombrar cada punto de entrada (descrito a continuación) ya que tiene menos control sobre qué funciones se exportan y no puede exportar las funciones por ordinal. TESTDLL1 y TESTDLL2 utilizan este método para exportar sus entradas.

Un método más eficaz (y el método utilizado por MFCxx.DLL) es exportar cada entrada a mano nombrando cada entrada en el archivo . DEF. Puesto que estamos exportando exportaciones selectivas desde nuestro archivo DLL (es decir, no todo), debemos decidir qué interfaces particulares deseamos exportar. Esto es difícil ya que debe especificar los nombres destrozados para el vinculador en forma de entradas en el archivo . DEF. No exporte ninguna clase C++ a menos que realmente necesite tener un enlace simbólico para ello.

Si ha intentado exportar clases C++ con un archivo . DEF antes, es posible que desee desarrollar una herramienta para generar esta lista automáticamente. Esto se puede hacer usando un proceso de link de dos etapas. Vincule el archivo DLL una vez sin exportaciones y permita que el vinculador genere un archivo . Archivo MAP. el. MAP archivo se puede utilizar para generar una lista de funciones que se deben exportar, por lo que con un poco de reorganización, se puede utilizar para generar sus entradas EXPORT para su . DEF. La lista de exportación para MFCxx.DLL y los archivos DLL de extensión OLE y MFC de base de datos, varios miles de personas en número, se generó con un proceso de este tipo (aunque no es completamente automático y requiere un ajuste manual de vez en cuando).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary

Un archivo DLL de `CWinApp`extensión MFC no tiene un objeto derivado propio; en su lugar, `CWinApp`debe funcionar con el objeto derivado de la aplicación cliente. Esto significa que la aplicación cliente posee la bomba de mensajes principal, el bucle inactivo, etc.

Si el archivo DLL de extensión de MFC necesita mantener datos `CDynLinkLibrary` adicionales para cada aplicación, puede derivar una nueva clase de y crearla en la rutina InitXxxDLL describe anteriormente. Cuando se ejecuta, el archivo DLL puede `CDynLinkLibrary` comprobar la lista de objetos de la aplicación actual para encontrar el archivo DLL de extensión MFC en particular.

### <a name="using-resources-in-your-dll-implementation"></a>Uso de recursos en la implementación de DLL

Como se mencionó anteriormente, la `CDynLinkLibrary` carga de recursos predeterminada recorrerá la lista de objetos que buscan el primer archivo EXE o DLL que tiene el recurso solicitado. Todas las API de MFC, así `AfxFindResourceHandle` como todo el código interno se usa para recorrer la lista de recursos para buscar cualquier recurso, independientemente de dónde pueda residir.

Si solo desea cargar recursos desde un lugar `AfxGetResourceHandle` específico, use las API y `AfxSetResourceHandle` guarde el identificador antiguo y establezca el nuevo identificador. Asegúrese de restaurar el identificador de recurso antiguo antes de volver a la aplicación de cliente. El ejemplo TESTDLL2 utiliza este enfoque para cargar explícitamente un menú.

Recorrer la lista tiene la desventaja de que es un proceso un poco más lento y requiere administrar intervalos de identificadores de recursos. Tiene la ventaja de que una aplicación cliente que se vincula a varios archivos DLL de extensión MFC puede usar cualquier recurso proporcionado por DLL sin tener que especificar el identificador de instancia de DLL. `AfxFindResourceHandle` es una API que se usa para recorrer la lista de recursos a fin de buscar una coincidencia determinada. Para ello, utiliza el nombre y el tipo de recurso, y devuelve el identificador de recurso donde se encontró por primera vez (o el valor NULL).

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Escribir una aplicación que use la versión DE DLL

### <a name="application-requirements"></a>Requisitos de la aplicación

Una aplicación que usa la versión compartida de MFC debe seguir algunas reglas simples:

- Debe tener `CWinApp` un objeto y seguir las reglas estándar para una bomba de mensajes.

- Debe compilarse con un conjunto de indicadores del compilador necesarios (consulte a continuación).

- Debe vincularse con las bibliotecas de importación de MFCxx. Al establecer los indicadores del compilador necesarios, los encabezados MFC determinan en tiempo de vínculo con qué biblioteca debe vincular la aplicación.

- Para ejecutar el archivo ejecutable, MFCxx.DLL debe estar en la ruta de acceso o en el directorio del sistema de Windows.

### <a name="building-with-the-development-environment"></a>Construcción con el entorno de desarrollo

Si está utilizando el archivo makefile interno con la mayoría de los valores predeterminados estándar, puede cambiar fácilmente el proyecto para compilar la versión DLL.

En el paso siguiente se supone que tiene una aplicación MFC que funciona correctamente vinculada con NAFXCWD. LIB (para depuración) y NAFXCW. LIB (para retail) y desea convertirlo para usar la versión compartida de la biblioteca MFC. Está ejecutando el entorno de Visual C++ y tiene un archivo de proyecto interno.

1. En el menú **Proyectos** , haga clic en **Propiedades**. En la página **General** en **Valores predeterminados**del proyecto , establezca Microsoft Foundation Classes en **Use MFC in a Shared DLL** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Edificio con NMAKE

Si está utilizando la característica makefile externa de Visual C++, o está utilizando NMAKE directamente, tendrá que editar su archivo make para admitir las opciones del compilador y del vinculador

Indicadores del compilador necesarios:

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

Los encabezados MFC estándar necesitan que se defina este símbolo:

- **/MD** La aplicación debe utilizar la versión DLL de la biblioteca en tiempo de ejecución de C

Todos los demás indicadores del compilador siguen los valores predeterminados de MFC (por ejemplo, _DEBUG para la depuración).

Edite la lista de bibliotecas del vinculador. Cambiar NAFXCWD. LIB a MFCxxD.LIB y cambiar NAFXCW. LIB a MFCxx.LIB. Reemplace LIBC. LIB con MSVCRT. Lib. Al igual que con cualquier otra biblioteca MFC, es importante que MFCxxD.LIB se coloque **antes** que las bibliotecas en tiempo de ejecución de C.

Opcionalmente, agregue **/D_AFXDLL** a las opciones del compilador de recursos comerciales y de depuración (la que realmente compila los recursos con **/R**). Esto hace que el ejecutable final sea más pequeño compartiendo los recursos que están presentes en los archivos DLL de MFC.

Se requiere una reconstrucción completa después de realizar estos cambios.

### <a name="building-the-samples"></a>Crear los ejemplos

La mayoría de los programas de ejemplo MFC se pueden compilar desde Visual C++ o desde un ARCHIVO MAKEFILE compatible con NMAKE compartido desde la línea de comandos.

Para convertir cualquiera de estos ejemplos para utilizar MFCxx.DLL, puede cargar el archivo . MAK en Visual C++ y establezca las opciones de proyecto como se describió anteriormente. Si está utilizando la compilación NMAKE, puede especificar "AFXDLL-1" en la línea de comandos NMAKE y que compilará el ejemplo mediante las bibliotecas MFC compartidas.

El ejemplo de conceptos avanzados de MFC [DLLHUSK](../overview/visual-cpp-samples.md) se compila con la versión DLL de MFC. Este ejemplo no solo ilustra cómo compilar una aplicación vinculada a MFCxx.DLL, sino que también ilustra otras características de la opción de empaquetado DLL de MFC, como los archivos DLL de extensión de MFC que se describen más adelante en esta nota técnica.

### <a name="packaging-notes"></a>Notas de embalaje

La versión comercial de los archivos DLL (MFCxx[U]. DLL) son libremente redistribuibles. La versión de depuración de los archivos DLL no se puede redistribuir libremente y solo se debe usar durante el desarrollo de la aplicación.

Los archivos DLL de depuración se proporcionan con información de depuración. Mediante el depurador de Visual C++, puede realizar un seguimiento de la ejecución de la aplicación, así como del archivo DLL. Los archivos DLL de versión (MFCxx[U]. DLL) no contienen información de depuración.

Si personaliza o reconstruye los archivos DLL, debe llamarlos algo distinto de "MFCxx" El archivo MFC SRC de MFC. MAK describe las opciones de compilación y contiene la lógica para cambiar el nombre del archivo DLL. Es necesario cambiar el nombre de los archivos, ya que estos archivos DLL son potencialmente compartidos por muchas aplicaciones MFC. Tener la versión personalizada de los archivos DLL de MFC reemplazar los instalados en el sistema puede interrumpir otra aplicación MFC mediante los archivos DLL de MFC compartidos.

No se recomienda volver a generar los archivos DLL de MFC.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Cómo se implementa MFCxx.DLL

En la sección siguiente se describe cómo se implementa el archivo DLL de MFC (MFCxx.DLL y MFCxxD.DLL). Comprender los detalles aquí tampoco es importante si todo lo que desea hacer es usar el archivo DLL de MFC con la aplicación. Los detalles aquí no son esenciales para entender cómo escribir un archivo DLL de extensión MFC, pero comprender esta implementación puede ayudarle a escribir su propio archivo DLL.

### <a name="implementation-overview"></a>Resumen de la implementación

El archivo DLL de MFC es realmente un caso especial de un archivo DLL de extensión de MFC como se describe anteriormente. Tiene un gran número de exportaciones para un gran número de clases. Hay algunas cosas adicionales que hacemos en el archivo DLL de MFC que lo hacen aún más especial que un archivo DLL de extensión MFC normal.

### <a name="win32-does-most-of-the-work"></a>Win32 hace la mayor parte del trabajo

La versión de 16 bits de MFC necesitaba una serie de técnicas especiales, incluidos los datos por aplicación en el segmento de pila, segmentos especiales creados por un código de ensamblado de 80 x 86, contextos de excepción por proceso y otras técnicas. Win32 admite directamente datos por proceso en un archivo DLL, que es lo que desea la mayor parte del tiempo. En su mayor parte MFCxx.DLL es sólo NAFXCW. LIB empaquetado en un archivo DLL. Si nos fijamos en el código fuente de MFC, encontrará muy pocas #ifdef _AFXDLL, ya que hay muy pocos casos especiales que deben realizarse. Los casos especiales que hay son específicamente para tratar con Win32 en Windows 3.1 (también conocido como Win32s). Win32s no admite datos DLL por proceso directamente, por lo que el archivo DLL de MFC debe usar las API de Win32 de almacenamiento local de subprocesos (TLS) para obtener datos locales de proceso.

### <a name="impact-on-library-sources-additional-files"></a>Impacto en las fuentes de la biblioteca, archivos adicionales

El impacto de la **versión _AFXDLL** en los orígenes y encabezados normales de la biblioteca de clases MFC es relativamente menor. Hay un archivo de versión especial (AFXV_DLL. H) así como un archivo de encabezado adicional (AFXDLL_. H) incluido por el AFXWIN principal. Encabezado H. El AFXDLL_. El encabezado `CDynLinkLibrary` H incluye la clase `_AFXDLL` y otros detalles de implementación de las aplicaciones y los archivos DLL de extensión MFC. El AFXDLLX. El encabezado H se proporciona para compilar archivos DLL de extensión MFC (consulte más arriba para obtener más información).

Los orígenes normales de la biblioteca MFC en `_AFXDLL` MFC SRC tienen algún código condicional adicional bajo el #ifdef. Un archivo de origen adicional (DLLINIT. CPP) contiene el código de inicialización DLL adicional y otro pegamento para la versión compartida de MFC.

Para compilar la versión compartida de MFC, se proporcionan archivos adicionales. (Consulte a continuación para obtener más información sobre cómo compilar el archivo DLL.)

- Dos. Los archivos DEF se utilizan para exportar los puntos de entrada DLL de MFC para las versiones de depuración (MFCxxD.DEF) y versión (MFCxx.DEF) del archivo DLL.

- Un. Archivo RC (MFCDLL. RC) contiene todos los recursos ESTÁNDAR de MFC y un recurso VERSIONINFO para el archivo DLL.

- Un. Archivo CLW (MFCDLL. CLW) se proporciona para permitir la exploración de las clases MFC mediante ClassWizard. Nota: esta característica no es particular para la versión DLL de MFC.

### <a name="memory-management"></a>Administración de la memoria

Una aplicación que usa MFCxx.DLL utiliza un asignador de memoria común proporcionado por MSVCRTxx.DLL, el archivo DLL compartido de tiempo de ejecución de C. La aplicación, los archivos DLL de extensión MFC y los propios archivos DLL de MFC usan este asignador de memoria compartida. Mediante el uso de un archivo DLL compartido para la asignación de memoria, los archivos DLL de MFC pueden asignar memoria que la aplicación libera más adelante o viceversa. Dado que tanto la aplicación como el archivo DLL deben usar el mismo asignador, no debe invalidar el operador global C++ **new** o **el operador delete**. Las mismas reglas se aplican al resto de las rutinas de asignación de memoria en tiempo de ejecución de C (como **malloc,** **realloc,** **free**y otras).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Ordinales y nombres de clase __declspec(dllexport) y DLL

No usamos `class` la funcionalidad **__declspec(dllexport)** del compilador C++. En su lugar, se incluye una lista de exportaciones con los orígenes de la biblioteca de clases (MFCxx.DEF y MFCxxD.DEF). Solo se exportan estos conjuntos selectos de puntos de entrada (funciones y datos). Otros símbolos, como las clases o funciones de implementación privada smfc, no se exportan Todas las exportaciones se realizan por ordinal sin un nombre de cadena en la tabla de nombres residentes o no residentes.

El `class` uso de **__declspec(dllexport)** puede ser una alternativa viable para crear archivos DLL más pequeños, pero en el caso de un archivo DLL grande como MFC, el mecanismo de exportación predeterminado tiene límites de eficiencia y capacidad.

Lo que todo esto significa es que podemos empaquetar una gran cantidad de funcionalidad en la versión MFCxx.DLL que es sólo alrededor de 800 KB sin comprometer mucha ejecución o velocidad de carga. MFCxx.DLL habría sido 100K más grande si no se hubiera utilizado esta técnica. Esto también permite añadir puntos de entrada adicionales al final del archivo . DEF para permitir un control de versiones simple sin comprometer la velocidad y la eficiencia de tamaño de la exportación por ordinal. Las revisiones de versiones principales de la biblioteca de clases MFC cambiarán el nombre de la biblioteca. Es decir, MFC30. DLL es el archivo DLL redistribuible que contiene la versión 3.0 de la biblioteca de clases MFC. Una actualización de este archivo DLL, por ejemplo, en un hipotético MFC 3.1, el archivo DLL se denominaría MFC31. DLL en su lugar. Una vez más, si modifica el código fuente de MFC para generar una versión personalizada del archivo DLL de MFC, use un nombre diferente (y preferiblemente uno sin "MFC" en el nombre).

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
