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
ms.openlocfilehash: fda256043027dbff249cedf490b150b6ad30a5fb
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611105"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: Versión de DLL de MFC

Esta nota describe cómo puede usar MFCxx.DLL y MFCxxD.DLL (donde x es el número de versión MFC) comparten las bibliotecas de vínculos dinámicos con las aplicaciones MFC y archivos DLL de extensión MFC. Para obtener más información sobre archivos DLL de MFC estándar, consulte [utilizar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Esta nota técnica trata tres aspectos de los archivos DLL. Los dos últimos son para los usuarios más avanzados:

- [Cómo crear un archivo DLL de extensión de MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Cómo crear una aplicación MFC utiliza la versión DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Cómo la MFC compartido bibliotecas de vínculos dinámicos se implementan.](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Si está interesado en crear un archivo DLL utiliza MFC que puede usarse con aplicaciones no basados en MFC (Esto se denomina una DLL de MFC normal), consulte [Nota técnica 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Información general de soporte técnico de MFCxx.DLL: Terminología y los archivos

**Archivo DLL de MFC estándar**: Usar un archivo DLL MFC para crear un archivo DLL independiente con algunas de las clases MFC. A través del límite de la aplicación o DLL interfaces son de "C" y la aplicación cliente no tiene que ser una aplicación MFC.

Esta es la versión de compatibilidad con DLL de MFC 1.0 admitido. Se describe en [Nota técnica 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) y el ejemplo de conceptos avanzados de MFC [DLLScreenCap](../overview/visual-cpp-samples.md).

> [!NOTE]
> A partir de Visual C++ versión 4.0, el término **USRDLL** está obsoleto y se ha reemplazado por una DLL de MFC normal que se vincule estáticamente a MFC. También puede crear a una DLL de MFC que se vincule dinámicamente a MFC normal.

MFC 3.0 (y versiones posteriores) es compatible con archivos DLL de MFC estándar con toda la funcionalidad nueva, incluidas las clases OLE y la base de datos.

**AFXDLL**: También se conoce como la versión compartida de las bibliotecas MFC. Se trata de la nueva compatibilidad DLL que se agregó en MFC 2.0. La propia biblioteca MFC es un número de archivos DLL (descrito a continuación) y una aplicación cliente o el archivo DLL se vincula dinámicamente los archivos DLL que requiere. Las interfaces a través del límite de la aplicación o DLL son C++/MFC interfaces de clases. La aplicación cliente debe ser una aplicación MFC. Esto es compatible con todas las funciones de MFC 3.0 (excepción: UNICODE no se admite para las clases de base de datos).

> [!NOTE]
> A partir de Visual C++ versión 4.0, este tipo de archivo DLL se conoce como un "archivo DLL de extensión."

Esta nota usará MFCxx.DLL para hacer referencia a todo el conjunto de DLL de MFC, que incluye:

- Depuración: MFCxxD.DLL (combinada) y MFCSxxD.LIB (estático).

- Versión: MFCxx.DLL (combinada) y MFCSxx.LIB (estático).

- Depuración de Unicode: MFCxxUD.DLL (combinada) y MFCSxxD.LIB (estático).

- Versión de Unicode: MFCxxU.DLL (combinada) y MFCSxxU.LIB (estático).

> [!NOTE]
> El MFCSxx [U] [D]. Lib se utiliza en junto con la MFC archivos DLL compartidos. Estas bibliotecas contienen código que debe vincularse estáticamente para la aplicación o DLL.

Vínculos de una aplicación a las bibliotecas de importación correspondiente:

- Depuración: MFCxxD.LIB

- Versión: MFCxx.LIB

- Depuración de Unicode: MFCxxUD.LIB

- Versión de Unicode: MFCxxU.LIB

Una "DLL de extensión MFC" es una DLL que se basa en MFCxx.DLL (o la MFC otra archivos DLL compartidos). Aquí la arquitectura de componentes MFC se activa. Si derivar una clase útil de una clase MFC o crea otro kit de herramientas de MFC similar, puede colocarlo en un archivo DLL. Que el archivo DLL utiliza MFCxx.DLL, como hace la aplicación cliente ultimate. Esto permite que las clases de hoja reutilizables, clases base reutilizables y clases de documento/vista reutilizables.

## <a name="pros-and-cons"></a>Ventajas y desventajas

¿Por qué debería usar la versión compartida de MFC

- Uso de la biblioteca compartida puede producir aplicaciones más pequeñas (una aplicación mínima que utiliza la mayor parte de la biblioteca MFC es menor que 10K).

- La versión compartida de MFC es compatible con archivos DLL de extensión de MFC y archivos DLL de MFC estándar.

- Crear una aplicación que usa las bibliotecas MFC compartidas es más rápido que crear una aplicación MFC vinculada estáticamente, ya no es necesario vincular MFC. Esto es especialmente cierto en **depurar** compilaciones donde el vinculador debe compactar la información de depuración, mediante la vinculación con un archivo DLL que ya contiene la información de depuración, hay menos información de depuración para compactar dentro de la aplicación.

¿Por qué no debe utilizarse la versión compartida de MFC:

- Una aplicación que utiliza la biblioteca compartida de trasvase de registros requiere que envíe MFCxx.DLL (y otros) biblioteca con el programa. MFCxx.DLL es redistribuir libremente como muchos archivos DLL, pero todavía debe instalar la DLL en el programa de instalación. Además, se debe enviar el MSVCRTxx.DLL, que contiene la biblioteca en tiempo de ejecución de C que se utiliza tanto el programa y los mismos archivos DLL de MFC.

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Cómo escribir un archivo DLL de extensión MFC

Una DLL de extensión de MFC es un archivo DLL que contiene las clases y funciones escritas para adornar la funcionalidad de las clases MFC. Una DLL de extensión MFC utiliza los archivos DLL de MFC compartido en la misma manera que una aplicación utiliza, con algunas consideraciones adicionales:

- El proceso de compilación es similar a la creación de una aplicación que usa las bibliotecas compartidas de MFC con unos adicionales del compilador y las opciones del vinculador.

- Una DLL de extensión MFC no tiene un `CWinApp`-clase derivada.

- Una DLL de extensión MFC debe proporcionar un especial `DllMain`. AppWizard proporciona una `DllMain` función que se puede modificar.

- Una DLL de extensión MFC suelen proporcionar una rutina de inicialización para crear un `CDynLinkLibrary` si desea que un archivo DLL de la extensión MFC exportar `CRuntimeClass`í o recursos a la aplicación. Una clase derivada de `CDynLinkLibrary` se pueden utilizar si se deben mantener los datos por aplicación mediante el archivo DLL de extensión MFC.

Estas consideraciones se describen más detalladamente a continuación. También debe consultar el ejemplo de conceptos avanzados [DLLHUSK](../overview/visual-cpp-samples.md) desde que muestra:

- Creación de una aplicación mediante las bibliotecas compartidas. (DLLHUSK. EXE es una aplicación MFC que se vincule dinámicamente a las bibliotecas MFC, así como otros archivos DLL).

- Creación de un archivo DLL de extensión MFC. (Tenga en cuenta las marcas especiales como `_AFXEXT` que se usan en la creación de un archivo DLL de extensión MFC)

- Dos ejemplos de archivos DLL de extensión de MFC. Muestra la estructura básica de una DLL de extensión MFC con exportaciones limitadas (TESTDLL1) y la otra muestra la exportación de una interfaz de clase completa (TESTDLL2).

La aplicación cliente y las DLL de extensión MFC deben usar la misma versión de MFCxx.DLL. Debe seguir la convención de DLL de MFC y proporcionar una depuración y venta por menor (/Release) versión de la DLL de extensión MFC. Esto permite que los programas cliente para generar versiones de depuración y comerciales de sus aplicaciones y vincularlas con la depuración adecuados o una versión comercial de todos los archivos DLL.

> [!NOTE]
>  Dado que C++ daños en el nombre y los problemas de exportación, la lista de exportación de un archivo DLL de extensión MFC puede ser diferente entre las versiones de depuración y comerciales de la misma DLL y archivos DLL para distintas plataformas. El minorista MFCxx.DLL con aproximadamente 2.000 puntos de entrada exportados; la depuración MFCxxD.DLL ha exportado 3000 unos puntos de entrada.

### <a name="quick-note-on-memory-management"></a>Nota rápida sobre la administración de memoria

La sección titulada "Administración de memoria", casi al final de esta nota técnica, describe la implementación de MFCxx.DLL con la versión compartida de MFC. La información que necesita saber para implementar solo una extensión MFC que dll se describe aquí.

MFCxx.DLL y todas las DLL de extensión MFC cargadas en el espacio de direcciones de la aplicación de cliente usará el mismo asignador de memoria, la carga de recursos y otros Estados "globales" de MFC como si estuvieran en la misma aplicación. Esto es importante porque las bibliotecas DLL que no son de MFC y archivos DLL de MFC estándar vinculados estáticamente a MFC realizan funciones exactamente opuestas y tienen cada sus archivos DLL asigna fuera de su propio bloque de memoria.

Si un archivo DLL de extensión MFC asigna memoria, esta memoria puede combinarse libremente con cualquier otro objeto asignado por la aplicación. Además, si se bloquea una aplicación que usa las bibliotecas compartidas de MFC, la protección del sistema operativo mantendrá la integridad de cualquier otra aplicación MFC que comparta el archivo DLL.

De forma similar, otros Estados "globales" de MFC, como el archivo ejecutable actual para cargar los recursos, también se comparten entre la aplicación cliente y todos los archivos DLL de extensión MFC, así como MFCxx.DLL propio.

### <a name="building-an-mfc-extension-dll"></a>Creación de un archivo DLL de extensión MFC

Puede usar el Asistente para aplicaciones para crear un proyecto de DLL de extensión MFC, y generará automáticamente el compilador adecuado y la configuración del vinculador. Era generar también un `DllMain` función que se puede modificar.

Si va a convertir un proyecto existente a un archivo DLL de extensión MFC, comience con las reglas estándar para la creación de una aplicación con la versión compartida de MFC y luego haga lo siguiente:

- Agregar **/D_AFXEXT** a las marcas de compilador. En el cuadro de diálogo Propiedades del proyecto, seleccione el nodo C o C++. A continuación, seleccione la categoría de preprocesador. Agregar `_AFXEXT` al campo definir Macros, separando cada uno de los elementos con punto y coma.

- Quitar el **/Gy** modificador del compilador. En el cuadro de diálogo Propiedades del proyecto, seleccione el nodo C o C++. A continuación, seleccione la categoría de generación de código. Asegúrese de que no está habilitada la opción "Habilitar vinculación en el nivel de función". Así resultará más fácil exportar clases porque el vinculador no quitará las funciones sin referencias. Si el proyecto original se usa para compilar normal MFC DLL vinculados estáticamente a MFC, cambio el **/MT [d]** opción del compilador para **/MD [d]**.

- Creación de una biblioteca de exportación con el **/DLL** opción de vínculo. Se establecerá cuando se crea un nuevo destino, especificando la biblioteca de vínculos dinámicos Win32 como el tipo de destino.

### <a name="changing-your-header-files"></a>Cambiar los archivos de encabezado

El objetivo de un archivo DLL de extensión MFC es normalmente exportar alguna funcionalidad común a una o varias aplicaciones que pueden usar esa funcionalidad. Esto se reduce a la exportación de las clases y funciones globales que están disponibles para las aplicaciones cliente.

Para ello debe asegurarse de que cada una de las funciones miembro está marcado como de importación o exportación según corresponda. Esto requiere declaraciones especiales: `__declspec(dllexport)` y `__declspec(dllimport)`. Cuando se utilizan las clases para las aplicaciones cliente, que desea que se puede declarar como `__declspec(dllimport)`. Cuando se está compilando el propio archivo DLL de extensión de MFC, debe declararse como `__declspec(dllexport)`. Además, las funciones deben realmente exportarse, para que los programas cliente enlazan con ellos en tiempo de carga.

Para exportar toda la clase, use `AFX_EXT_CLASS` en la definición de clase. Esta macro se define mediante el marco de trabajo como `__declspec(dllexport)` cuando `_AFXDLL` y `_AFXEXT` está definido, pero se define como `__declspec(dllimport)` cuando `_AFXEXT` no está definido. `_AFXEXT` como se describió anteriormente, solo se define al crear el archivo DLL de extensión MFC. Por ejemplo:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>No exporte toda la clase

A veces es posible que desee exportar a solo los miembros individuales necesarios de la clase. Por ejemplo, si va a exportar un `CDialog`-clase derivada, solo es posible que deba exportar el constructor y el `DoModal` llamar. Puede exportar a estos miembros mediante la DLL. Archivo DEF, pero también puede usar `AFX_EXT_CLASS` en la misma manera en los miembros individuales que desea exportar.

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

Al hacerlo, es posible que experimenta un problema adicional porque ya no va a exportar a todos los miembros de la clase. El problema radica en la forma en que funcionan las macros MFC. Algunas de las macros de aplicación auxiliar de MFC realmente declaran ni definen a miembros de datos. Por lo tanto, estos miembros de datos también debe exportarse desde el archivo DLL.

Por ejemplo, la macro DECLARE_DYNAMIC se define como sigue cuando se crea un archivo DLL de extensión MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

La línea que comienza "estático `AFX_DATA`" se declara un objeto estático dentro de la clase. Para exportar correctamente esta clase y tener acceso a la información en tiempo de ejecución desde un cliente. EXE, deberá exportar este objeto estático. Dado que el objeto estático se declara con el modificador `AFX_DATA`, solo necesita definir `AFX_DATA` sea `__declspec(dllexport)` al compilar el archivo DLL y definirlo como `__declspec(dllimport)` al compilar el archivo ejecutable cliente.

Como se dijo anteriormente, `AFX_EXT_CLASS` ya está definida de esta manera. Deberá volver a definir `AFX_DATA` sea el mismo que `AFX_EXT_CLASS` en torno a la definición de clase.

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

MFC utiliza siempre la `AFX_DATA` símbolos en los elementos de datos define dentro de las macros, por lo que esta técnica funcionará para todos estos escenarios. Por ejemplo, funcionará para DECLARE_MESSAGE_MAP.

> [!NOTE]
> Si va a exportar toda la clase en lugar de los miembros seleccionados de la clase, se exportan automáticamente los miembros de datos estáticos.

Puede usar la misma técnica para exportar automáticamente la `CArchive` operador de extracción para las clases que use las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. Exportar el operador archive encerrando las declaraciones de clase (ubicado en el. Archivo de H) con el código siguiente:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>Limitaciones de _AFXEXT

Puede usar el _**AFXEXT** símbolos de preprocesador para la extensión siempre y cuando no tiene varias capas de DLL de extensión MFC de DLL MFC. Si tiene la extensión de MFC archivos DLL que llamar o derivar desde clases en su propia extensión MFC archivos DLL, que se derivan de las clases de MFC, debe utilizar su propio símbolo de preprocesador para evitar la ambigüedad.

El problema es que en Win32, debe declarar explícitamente todos los datos como `__declspec(dllexport)` si se van a exportarse desde un archivo DLL, y `__declspec(dllimport)` si se van a importar desde un archivo DLL. Al definir `_AFXEXT`, los encabezados de MFC, asegúrese de que `AFX_EXT_CLASS` está definida correctamente.

Cuando hay varios niveles, un símbolo como `AFX_EXT_CLASS` no es suficiente, puesto que un archivo DLL de extensión MFC puede exportar clases nuevas, así como importar otras clases desde otro archivo DLL de extensión MFC. Para resolver este problema, utilice un símbolo de preprocesador especial que indica que se está compilando el archivo DLL, frente al uso de la DLL. Por ejemplo, imagine dos archivos DLL de extensión MFC, A.DLL y B.DLL. Cada uno de ellos exporta algunas clases en A.H y B.H, respectivamente. B.DLL utiliza las clases de A.DLL. Los archivos de encabezado sería algo parecido a esto:

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

A.DLL se genera con **/DA_IMPL** y B.DLL se genera con **/DB_IMPL**. Mediante el uso de símbolos independientes para cada DLL, CExampleB se exporta y CExampleA se importa al compilar B.DLL. CExampleA se exporta al generar A.DLL y se importa al utiliza B.DLL (o algún otro cliente).

Este tipo de disposición en capas no se puede realizar cuando se usa el método integrado `AFX_EXT_CLASS` y `_AFXEXT` símbolos de preprocesador. La técnica descrita anteriormente soluciona este problema en una manera que el mecanismo de MFC usa al generar su archivos DLL de extensión MFC de red, base de datos y OLE.

### <a name="not-exporting-the-entire-class"></a>No exporte toda la clase

De nuevo, tendrá que tener especial cuidado cuando no se exporta una clase entera. Tiene que asegurarse de que los elementos de datos necesarios creados por las macros MFC se exportan correctamente. Esto puede hacerse mediante la definición de volver a `AFX_DATA` macro específica de la clase. Esto debe hacerse siempre que no se exporte toda la clase.

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

Este es el código exacto que se debe colocar en el archivo de código fuente principal para el archivo DLL de extensión MFC. Debe venir después de que incluye el estándar. Tenga en cuenta que cuando se usa el Asistente para aplicaciones para crear archivos de inicio para un archivo DLL de extensión MFC, proporciona un `DllMain` para usted.

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

La llamada a `AfxInitExtensionModule` captura las clases de tiempo de ejecución de módulos (`CRuntimeClass` estructuras), así como los generadores de objetos (`COleObjectFactory` objetos) para su uso posterior cuando la `CDynLinkLibrary` se crea el objeto. La llamada (opcional) a `AfxTermExtensionModule` permite MFC limpiar el archivo DLL de extensión MFC cuando se desasocia de cada proceso (que tiene lugar cuando se cierra el proceso, o cuando se descarga el archivo DLL como resultado de una `FreeLibrary` llamar a) desde el archivo DLL de extensión MFC. Desde la mayoría de extensión de MFC archivos DLL no se cargaron dinámicamente (por lo general, están vinculadas a través de sus bibliotecas de importación), la llamada a `AfxTermExtensionModule` normalmente no es necesario.

Si la aplicación se carga y libera la DLL de extensión MFC dinámicamente, no olvide llamar a `AfxTermExtensionModule` como se indicó anteriormente. También asegúrese de usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de funciones de Win32 `LoadLibrary` y `FreeLibrary`) si la aplicación usa varios subprocesos o si carga dinámicamente un archivo DLL de extensión MFC. Uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión MFC no dañe el estado global de MFC.

El archivo de encabezado AFXDLLX. H contiene definiciones especiales para las estructuras utilizadas en archivos DLL de extensión MFC, como la definición de `AFX_EXTENSION_MODULE` y `CDynLinkLibrary`.

Global *extensionDLL* debe declararse como se muestra. A diferencia de la versión de 16 bits de MFC, puede asignar memoria y llamar a funciones de MFC durante este tiempo, puesto que MFCxx.DLL está completamente inicializado en el momento en el `DllMain` se llama.

### <a name="sharing-resources-and-classes"></a>Compartir recursos y clases

Archivos DLL de extensión MFC simple solo necesita exportar algunas funciones de bajo ancho de banda para la aplicación cliente y nada más. Más archivos DLL de uso intensivo de interfaz de usuario que desee exportar los recursos y las clases de C++ a la aplicación cliente.

La exportación de recursos se realiza mediante una lista de recursos. En cada aplicación es una lista vinculada individualmente de `CDynLinkLibrary` objetos. Cuando se busca un recurso, la mayoría de las implementaciones MFC estándar que cargan recursos buscan primera en el módulo de recursos actual (`AfxGetResourceHandle`) y no se ha encontrado el recorrido de la lista de `CDynLinkLibrary` objetos al intentar cargar el recurso solicitado.

Creación dinámica de objetos de C++ le asigna un nombre de clase de C++ es similar. El mecanismo de deserialización de objetos de MFC debe tener todos los `CRuntimeClass` objetos registran para poder reconstruir creando dinámicamente objetos C++ del tipo requerido en función de lo que estaba almacenado anteriormente.

Si desea que la aplicación cliente para utilizar clases en el archivo DLL de extensión MFC `DECLARE_SERIAL`, será necesario exportar las clases para que sea visible para la aplicación cliente. Esto también se realiza al recorrer el `CDynLinkLibrary` lista.

En el caso del ejemplo de conceptos avanzados de MFC [DLLHUSK](../overview/visual-cpp-samples.md), la lista de aspecto similar al siguiente:

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

MFCxx.DLL es normalmente al final de la lista de clase y recursos. MFCxx.DLL incluye todos los recursos MFC estándares, incluidas las cadenas para todos los identificadores de comando estándar. Colocarlo en la cola de la lista de los archivos DLL y la aplicación cliente no tiene un su propia copia de los recursos MFC estándar, pero a se basan en los recursos compartidos de MFCxx.DLL en su lugar.

Combinar los recursos y los nombres de clase de todos los archivos DLL en el espacio de nombres de la aplicación cliente tiene la desventaja de que tener cuidado qué identificadores o nombres que elija. Por supuesto puede deshabilitar esta característica mediante la exportación no cualquiera los recursos o un `CDynLinkLibrary` objeto a la aplicación cliente. El [DLLHUSK](../overview/visual-cpp-samples.md) ejemplo administra el espacio de nombres de recurso compartido mediante el uso de varios archivos de encabezado. Consulte [Nota técnica 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) para obtener más sugerencias sobre el uso de archivos de recursos compartidos.

### <a name="initializing-the-dll"></a>Inicializar el archivo DLL

Como se mencionó anteriormente, normalmente le interesará crear un `CDynLinkLibrary` objeto con el fin de exportar sus recursos y clases a la aplicación cliente. Deberá proporcionar un punto de entrada exportados para inicializar el archivo DLL. Como mínimo, se trata de una rutina void que no toma ningún argumento y no devuelve nada, pero puede ser que desee.

Cada aplicación de cliente que desea usar el archivo DLL debe llamar a esta rutina de inicialización, si usa este enfoque. También puede asignar este `CDynLinkLibrary` objeto en su `DllMain` justo después de llamar a `AfxInitExtensionModule`.

La rutina de inicialización debe crear un `CDynLinkLibrary` objeto en el montón de la aplicación actual, conectado con la información del archivo DLL de extensión de MFC. Esto puede hacerse con lo siguiente:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

El nombre de la rutina, *InitXxxDLL* en este ejemplo, puede ser cualquier cosa que desee. No necesita ser **extern "C"**, pero si por lo que hace más fácil de mantener la lista de exportación.

> [!NOTE]
> Si utiliza el archivo DLL de extensión MFC desde una DLL de MFC normal, debe exportar esta función de inicialización. Esta función debe llamarse desde la DLL de MFC normal antes de utilizar recursos ni las clases de DLL de extensión MFC.

### <a name="exporting-entries"></a>Exportar las entradas

Es una manera sencilla de exportar las clases con `__declspec(dllimport)` y `__declspec(dllexport)` en cada clase y función global que desea exportar. Esto facilita mucho, pero es menos eficaz que el nombre de cada punto de entrada (se describe a continuación), ya que tiene menos control sobre qué funciones se exportan y no se puede exportar las funciones por ordinal. TESTDLL1 y TESTDLL2 utilizan este método para exportar sus entradas.

Un método más eficaz (y el método utilizado por MFCxx.DLL) son exportar cada entrada a mano asignando cada entrada en el. Archivo DEF. Puesto que nos estamos exportar exportaciones selectivas desde el archivo DLL (es decir, no todos los elementos), debemos decidir qué interfaces concreto que desee exportar. Esto es difícil, ya que debe especificar los nombres alterados al vinculador en el formulario de entradas en el. Archivo DEF. No exporte todas las clases de C++ a menos que realmente necesite tener un vínculo simbólico para él.

Si intentó exportar C++ las clases con una. Antes, es posible que desea desarrollar una herramienta para generar automáticamente esta lista de archivos DEF. Esto puede hacerse mediante un proceso de vinculación de dos fases. Vincula el archivo DLL una vez con ninguna exportación, y permite al vinculador que genere una. Archivo de asignación. El archivo. Archivo de asignación puede usarse para generar una lista de funciones que deben exportarse, por lo que con algunas reorganizar, puede utilizarse para generar las entradas de exportación para el. Archivo DEF. La lista de exportación para MFCxx.DLL y OLE y archivos DLL de extensión MFC de base de datos, varios miles de número, se generó con este proceso (aunque no es completamente automático y requiere algunos mano optimización reinician de vez en cuando).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary

Una DLL de extensión MFC no tiene un `CWinApp`-objeto propio derivado; en su lugar debe trabajar con el `CWinApp`-derivado de la aplicación cliente. Esto significa que la aplicación cliente posee el bombeo de mensajes principal, el bucle de inactividad y así sucesivamente.

Si el archivo DLL de extensión de MFC requiere mantener datos adicionales para cada aplicación, puede derivar una nueva clase de `CDynLinkLibrary` y crearla en el InitXxxDLL rutina se describe anteriormente. Cuando se ejecuta, el archivo DLL puede comprobar la lista actual de la aplicación de `CDynLinkLibrary` objetos que se va a buscar el correspondiente a ese archivo DLL de extensión MFC determinado.

### <a name="using-resources-in-your-dll-implementation"></a>Uso de recursos en su implementación de DLL

Como se mencionó anteriormente, la carga de recursos predeterminada le guiará a la lista de `CDynLinkLibrary` objetos busca el primer archivo EXE o DLL que tiene el recurso solicitado. Todas las API de MFC, así como todo el código interno usa `AfxFindResourceHandle` para recorrer la lista de recursos para encontrar cualquier recurso, independientemente de donde pueden residir.

Si desea cargar solo los recursos desde una ubicación específica, use las API `AfxGetResourceHandle` y `AfxSetResourceHandle` para guardar el identificador antiguo y establecer el nuevo identificador. Asegúrese de restaurar el identificador de recurso antiguo antes de volver a la aplicación de cliente. El ejemplo TESTDLL2 usa este enfoque para cargar explícitamente un menú.

Recorrer la lista tiene la desventaja de que es un proceso un poco más lento y requiere administrar intervalos de identificadores de recursos. Tiene la ventaja de que una aplicación cliente que se vincula a varios archivos DLL de extensión MFC puede usar cualquier recurso proporcionado por el archivo DLL sin tener que especificar el identificador de instancia del archivo DLL. `AfxFindResourceHandle` es una API que se usa para recorrer la lista de recursos a fin de buscar una coincidencia determinada. Para ello, utiliza el nombre y el tipo de recurso, y devuelve el identificador de recurso donde se encontró por primera vez (o el valor NULL).

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Escribir una aplicación que usa la versión de DLL

### <a name="application-requirements"></a>Requisitos de la aplicación

Una aplicación que usa la versión compartida de MFC debe seguir unas sencillas reglas:

- Debe tener un `CWinApp` de objetos y seguir las reglas estándares para una bomba de mensaje.

- Se debe compilar con un conjunto de marcas de compilador necesarias (ver abajo).

- Debe vincular con las bibliotecas de importación MFCxx. Al establecer las marcas de compilador necesarias, los encabezados de MFC determinan en tiempo de vinculación la biblioteca de la aplicación debe vincularse a.

- Para ejecutar el archivo ejecutable, debe ser MFCxx.DLL en la ruta de acceso o en el directorio del sistema de Windows.

### <a name="building-with-the-development-environment"></a>Creación con el entorno de desarrollo

Si usa el archivo MAKE interno con la mayoría de los valores predeterminados estándares, puede cambiar fácilmente el proyecto para compilar la versión DLL.

El paso siguiente supone que tiene una aplicación MFC funcionan correctamente vinculada con NAFXCWD. LIB (para depuración) y NAFXCW. LIB (para versión comercial) y desea convertirlo para usar la versión compartida de la biblioteca MFC. Ejecuta el entorno de Visual C++ y tiene un archivo de proyecto interno.

1. En el **proyectos** menú, haga clic en **propiedades**. En el **General** página **valores predeterminados del proyecto**, establezca Microsoft Foundation Classes en **utilizar MFC en un archivo DLL compartido** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Creación de NMAKE

Si va a usar la característica de archivo MAKE externo de Visual C++, o usa NMAKE directamente, debe editar el archivo MAKE para admitir opciones del compilador y vinculador

Marcas de compilador necesarias:

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

Los encabezados MFC estándar necesitan este símbolo definirse:

- **/MD** la aplicación debe utilizar la versión de DLL de la biblioteca de tiempo de ejecución de C

Todas las otras marcas del compilador siguen los valores predeterminados MFC (por ejemplo, _DEBUG para depuración).

Editar la lista del vinculador de bibliotecas. Cambio NAFXCWD. LIB en MFCxxD.LIB y cambiar NAFXCW. LIB MFCxx.LIB. Reemplace LIBC. LIB con MSVCRT. LIB. Igual que con cualquier otra biblioteca MFC es importante que se coloca MFCxxD.LIB **antes** las bibliotecas en tiempo de ejecución de C.

Opcionalmente, agregue **/D_AFXDLL** a sus comerciales y depuración opciones del compilador de recursos (lo que se compila realmente los recursos con **/R**). Esto hace que el archivo ejecutable final más pequeñas mediante el uso compartido de los recursos que se encuentran en los archivos DLL de MFC.

Una recompilación completa es necesaria una vez realizados estos cambios.

### <a name="building-the-samples"></a>Compilar los ejemplos

La mayoría de los programas de ejemplo MFC puede crearse desde Visual C++ o desde un archivo MAKE de NMAKE compatible compartido desde la línea de comandos.

Para convertir algunos de estos ejemplos para usar MFCxx.DLL, puede cargar el. MAK el archivo en Visual C++ y establecer las opciones de proyecto, como se describió anteriormente. Si usa la compilación NMAKE, puede especificar "AFXDLL = 1" en el NMAKE línea de comandos y que se compilará el ejemplo mediante las bibliotecas compartidas de MFC.

El ejemplo de conceptos avanzados [DLLHUSK](../overview/visual-cpp-samples.md) se ha creado con la versión DLL de MFC. Este ejemplo no solo muestra cómo crear una aplicación que se vincula con MFCxx.DLL, pero también muestra otras características de la opción de empaquetado de DLL de MFC, como se describe más adelante en esta nota técnica archivos DLL de extensión de MFC.

### <a name="packaging-notes"></a>Notas de empaquetado

La versión comercial de los archivos DLL (MFCxx [U]. DLL) son redistribuibles libremente. La versión de depuración de los archivos DLL no son redistribuible libremente y debe utilizarse solo durante el desarrollo de la aplicación.

La DLL de depuración se proporciona información de depuración. Con el depurador de Visual C++, puede realizar el seguimiento de ejecución de la aplicación, así como el archivo DLL. Los archivos DLL de versión (MFCxx [U]. DLL) no contienen información de depuración.

Si personaliza o volver a generar los archivos DLL, a continuación, debe llamar a ellos algo distinto de archivo "MFCxx" The MFC SRC MFCDLL. MAK describe las opciones de compilación y contiene la lógica para cambiar el nombre del archivo DLL. Cambiar el nombre de los archivos es necesario, ya que estos archivos DLL se comparten potencialmente muchas aplicaciones de MFC. Tener la versión personalizada de la sustitución de archivos DLL de MFC están instalados en el sistema pueden interrumpir otra aplicación MFC con las DLL de MFC compartido.

No se recomienda volver a generar los archivos DLL de MFC.

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> Cómo se implementa MFCxx.DLL

La siguiente sección describe cómo se implementa la DLL de MFC (MFCxx.DLL y MFCxxD.DLL). Comprender que los detalles aquí también no son importante si todo lo que desea hacer es utilizar la DLL de MFC con la aplicación. Los detalles aquí no son esenciales para entender cómo escribir un archivo DLL de extensión MFC, pero comprender esta implementación puede ayudarle a escribir su propio archivo DLL.

### <a name="implementation-overview"></a>Información general de implementación

La DLL de MFC es realmente un caso especial de una DLL de extensión de MFC, como se describió anteriormente. Tiene un gran número de exportaciones de un gran número de clases. Hay algunos aspectos adicionales que hacemos en la DLL de MFC que facilitan aún más especiales a un archivo DLL de extensión MFC regular.

### <a name="win32-does-most-of-the-work"></a>Win32 realiza la mayor parte del trabajo

La versión de 16 bits de MFC, necesita un número de técnicas especiales, incluidos los datos por aplicación en el segmento de pila, segmentos especiales creados por algún código de ensamblado de 80 x 86, contextos de excepción por proceso y otras técnicas. Win32 admite directamente por el procesamiento de datos en un archivo DLL, que es lo que desea que la mayoría del tiempo. La mayor parte MFCxx.DLL es simplemente NAFXCW. LIB empaquetado en un archivo DLL. Si observa el código fuente MFC, encontrará muy pocos _AFXDLL #ifdef, puesto que hay muy pocos casos especiales que deben realizarse. Los casos especiales que están hay específicamente para tratar con Win32 en 3.1 de Windows (también conocida como Win32s). Win32s no soporte por proceso DLL datos directamente por lo que la DLL de MFC debe usar el almacenamiento local de subprocesos (TLS), las API de Win32 para obtener datos de proceso local.

### <a name="impact-on-library-sources-additional-files"></a>Impacto en la biblioteca de fuentes, archivos adicionales

El impacto de la **_AFXDLL** versión en los orígenes de biblioteca de clases MFC y encabezados normal es relativamente pequeño. Hay un archivo de la versión especial (AFXV_DLL. (H), así como un archivo de encabezado adicional (AFXDLL_. (H) incluye la AFXWIN principal. Encabezado de H. El AFXDLL_. Incluye el encabezado de H el `CDynLinkLibrary` clase y otros detalles de implementación de ambos `_AFXDLL` aplicaciones y archivos DLL de extensión de MFC. El AFXDLLX. Encabezado H se proporciona para la creación de archivos DLL de extensión de MFC (vea más arriba para obtener más información).

Los orígenes de normales a la biblioteca MFC en MFC SRC tienen código condicional adicional en el `_AFXDLL` #ifdef. Un archivo de origen adicionales (DLLINIT. (CPP) contiene el código de inicialización de DLL adicional y otro adherencia para la versión compartida de MFC.

Para compilar la versión compartida de MFC, se proporcionan archivos adicionales. (Vea a continuación para obtener más información sobre cómo crear el archivo DLL).

- Dos. DEF (archivos) se usan para la exportación de los puntos de entrada de DLL de MFC para la depuración (MFCxxD.DEF) y versiones de lanzamiento (MFCxx.DEF) de la DLL.

- Un archivo. Archivo RC (MFCDLL. RC) contiene todos los recursos MFC estándares y un recurso VERSIONINFO para el archivo DLL.

- UN OBJETO. Archivo CLW (MFCDLL. CLW) se proporciona permitir el examen de MFC, clases con ClassWizard. Nota: esta característica no es específica de la versión DLL de MFC.

### <a name="memory-management"></a>Administración de memoria

Una aplicación mediante MFCxx.DLL usa un asignador de memoria común proporcionado por MSVCRTxx.DLL, el archivo DLL de C en tiempo de ejecución compartido. La aplicación, los archivos DLL de extensión MFC y así como los archivos DLL de MFC utilizan este asignador de memoria compartida. Mediante el uso de un archivo DLL compartido para la asignación de memoria, los archivos DLL de MFC puede asignar memoria que posteriormente se libera por la aplicación, o viceversa. Dado que la aplicación y el archivo DLL deben usar el mismo asignador, no debe reemplazar el C++ global **new (operador)** o **operador delete**. Las mismas reglas se aplican al resto de las rutinas de asignación de memoria en tiempo de ejecución de C (como **malloc**, **realloc**, **libre**etc.).

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>Los ordinales y clase __declspec (dllexport) y nombres de archivo DLL

No usamos la `class` **__declspec (dllexport)** funcionalidad de la C++ compilador. En su lugar, una lista de exportaciones se incluye con los orígenes de la biblioteca de clase (MFCxx.DEF y MFCxxD.DEF). Se exportan solo estos seleccione conjunto de puntos de entrada (funciones y datos). Otros símbolos, como las funciones de implementación privados de MFC o clases, no se exportan todas las exportaciones que se realizan por ordinal sin un nombre de cadena en la tabla de nombres residentes o no residentes.

Uso de `class` **__declspec (dllexport)** puede ser una alternativa viable para la creación de DLL más pequeñas, pero en el caso de una gran DLL como MFC, exportar el mecanismo predeterminado tiene la eficacia y capacidad de los límites.

¿Qué es esto significa que podemos empaqueta una gran cantidad de funcionalidad en la versión MFCxx.DLL que solo es de aproximadamente 800 KB sin poner en riesgo mucho la ejecución o la velocidad de carga. MFCxx.DLL habría sido mayor de 100 K esta técnica no se hubiera utilizado. Esto también hace posible agregar puntos de entrada adicionales al final de la. Archivo DEF para permitir el control de versiones simple sin poner en peligro la eficacia de velocidad y el tamaño de exportar por ordinal. Las revisiones de la versión principal de la biblioteca de clases MFC cambiará el nombre de la biblioteca. Es decir, MFC30. DLL es redistribuible archivo DLL que contiene la versión 3.0 de la biblioteca de clases MFC. Una actualización de este archivo DLL, por ejemplo, en una hipotética 3.1 de MFC, el archivo DLL se denominará MFC31. Archivo DLL en su lugar. Nuevamente, si modifica el código fuente MFC para generar una versión personalizada de la DLL de MFC, utilice un nombre diferente (y preferiblemente uno sin "MFC" en el nombre).

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
