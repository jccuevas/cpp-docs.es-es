---
title: Macros y funciones para administrar archivos dll
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: b27f8763b60dc7ce3ee074cad1365e7e1de3a7e6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426700"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Macros y funciones para administrar archivos dll

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exporta clases.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Proteger una función exportada en un archivo DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Proporciona compatibilidad con OLE desde un archivo DLL de MFC normal que se vincula dinámicamente a MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Proporciona compatibilidad con los sockets MFC desde un archivo DLL de MFC normal que se vincula dinámicamente a MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Obtiene el estado actual de la marca de estado por módulo.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Establece el estado del módulo antes de la inicialización o para restaurar el estado anterior del módulo después de la limpieza.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Inicializa el archivo DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|Establezca la marca de estado por módulo, que afecta al comportamiento de WinSxS de MFC.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Permite que MFC Limpie el archivo DLL de extensión de MFC cuando cada proceso se desasocie de la DLL.|

## <a name="afx_ext_class"></a>AFX_EXT_CLASS

Los [archivos dll de extensión de MFC](../../build/extension-dlls.md) utilizan la macro AFX_EXT_CLASS para exportar clases; los ejecutables que se vinculan al archivo DLL de extensión de MFC utilizan la macro para importar clases.

### <a name="remarks"></a>Observaciones

Con la macro AFX_EXT_CLASS, se pueden usar los mismos archivos de encabezado utilizados para generar el archivo DLL de extensión de MFC con los ejecutables que se vinculan a la DLL.

En el archivo de encabezado de la DLL, agregue la palabra clave AFX_EXT_CLASS a la declaración de la clase como se indica a continuación:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Para obtener más información, vea [exportar e importar mediante AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxv_dll. h

## <a name="afx_manage_state"></a>AFX_MANAGE_STATE

Llame a esta macro para proteger una función exportada en un archivo DLL.

### <a name="syntax"></a>Sintaxis

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parámetros

*pModuleState*<br/>
Puntero a una estructura de `AFX_MODULE_STATE`.

### <a name="remarks"></a>Observaciones

Cuando se invoca esta macro, *pModuleState* es el estado efectivo del módulo para el resto del ámbito contenedor inmediato. Cuando se sale del ámbito, el estado anterior del módulo efectivo se restaurará automáticamente.
La estructura `AFX_MODULE_STATE` contiene los datos globales del módulo, es decir, la parte del estado del módulo que se inserta o se extrae.

De forma predeterminada, MFC usa el identificador de recursos de la aplicación principal para cargar la plantilla de recursos. Si tiene una función exportada en un archivo DLL, como una que inicia un cuadro de diálogo en el archivo DLL, esta plantilla se almacena realmente en el módulo DLL. Debe cambiar el estado del módulo para que se utilice el identificador correcto. Puede hacerlo agregando el código siguiente al principio de la función:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Esto intercambia el estado actual del módulo con el estado devuelto desde [AfxGetStaticModuleState](#afxgetstaticmodulestate) hasta el final del ámbito actual.

Para obtener más información sobre los Estados de módulo y MFC, vea "administrar los datos de estado de los módulos MFC" en [crear nuevos documentos, ventanas y vistas](../creating-new-documents-windows-and-views.md) y [Nota técnica 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
>  Cuando MFC crea un contexto de activación para un ensamblado, usa [AfxWinInit](application-information-and-management.md#afxwininit) para crear el contexto y `AFX_MANAGE_STATE` para activarlo y desactivarlo. Tenga en cuenta también que `AFX_MANAGE_STATE` está habilitado para las bibliotecas estáticas de MFC, así como para los archivos dll de MFC, con el fin de permitir que el código MFC se ejecute en el contexto de activación adecuado seleccionado por el archivo DLL de usuario. Para obtener más información, vea [compatibilidad con los contextos de activación en el estado del módulo MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxstat_. h

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

Para la compatibilidad con OLE desde un archivo DLL de MFC normal que está vinculado dinámicamente a MFC, llame a esta función en la función `CWinApp::InitInstance` de la DLL de MFC normal para inicializar el archivo DLL de OLE de MFC.

### <a name="syntax"></a>Sintaxis

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Observaciones

El archivo DLL de OLE de MFC es un archivo DLL de extensión de MFC; para que un archivo DLL de extensión de MFC se pueda conectar a una cadena de `CDynLinkLibrary`, debe crear un objeto `CDynLinkLibrary` en el contexto de cada módulo que lo vaya a utilizar. `AfxOleInitModule` crea el objeto `CDynLinkLibrary` en el contexto del archivo DLL de MFC normal, de modo que se conecta a la cadena de objetos `CDynLinkLibrary` del archivo DLL de MFC normal.

Si va a compilar un control OLE y está utilizando `COleControlModule`, no debe llamar a `AfxOleInitModule` porque la función miembro `InitInstance` para `COleControlModule` llama a `AfxOleInitModule`.

### <a name="requirements"></a>Requisitos

**Encabezado**: \<afxdll_. h >

## <a name="afxnetinitmodule"></a>AfxNetInitModule

Para la compatibilidad con sockets MFC desde un archivo DLL de MFC normal que está vinculado dinámicamente a MFC, agregue una llamada a esta función en la función `CWinApp::InitInstance` de la DLL de MFC normal para inicializar el archivo DLL de sockets MFC.

### <a name="syntax"></a>Sintaxis

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Observaciones

La DLL de sockets de MFC es un archivo DLL de extensión de MFC; para que un archivo DLL de extensión de MFC se pueda conectar a una cadena de `CDynLinkLibrary`, debe crear un objeto `CDynLinkLibrary` en el contexto de cada módulo que lo vaya a utilizar. `AfxNetInitModule` crea el objeto `CDynLinkLibrary` en el contexto del archivo DLL de MFC normal, de modo que se conecta a la cadena de objetos `CDynLinkLibrary` del archivo DLL de MFC normal.

### <a name="requirements"></a>Requisitos

**Encabezado:** \<afxdll_. h >

## <a name="afxgetambientactctx"></a>AfxGetAmbientActCtx

Use esta función para obtener el estado actual de la marca de estado por módulo, que afecta al comportamiento de WinSxS de MFC.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del indicador de estado del módulo.

### <a name="remarks"></a>Observaciones

Cuando se establece la marca (que es el valor predeterminado) y un subproceso entra en un módulo MFC (vea [AFX_MANAGE_STATE](#afx_manage_state)), se activa el contexto del módulo.

Si no se establece la marca, el contexto del módulo no se activa en la entrada.

El contexto de un módulo se determina a partir de su manifiesto, normalmente incrustado en los recursos del módulo.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxcomctl32. h

## <a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState

Llame a esta función para establecer el estado del módulo antes de la inicialización o para restaurar el estado anterior del módulo después de la limpieza.

### <a name="syntax"></a>Sintaxis

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura de `AFX_MODULE_STATE`.

### <a name="remarks"></a>Observaciones

La estructura `AFX_MODULE_STATE` contiene los datos globales del módulo, es decir, la parte del estado del módulo que se inserta o se extrae.

De forma predeterminada, MFC usa el identificador de recursos de la aplicación principal para cargar la plantilla de recursos. Si tiene una función exportada en un archivo DLL, como una que inicia un cuadro de diálogo en el archivo DLL, esta plantilla se almacena realmente en el módulo DLL. Debe cambiar el estado del módulo para que se utilice el identificador correcto. Puede hacerlo agregando el código siguiente al principio de la función:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Esto intercambia el estado actual del módulo con el estado devuelto desde `AfxGetStaticModuleState` hasta el final del ámbito actual.

Para obtener más información sobre los Estados de módulo y MFC, vea "administrar los datos de estado de los módulos MFC" en [crear nuevos documentos, ventanas y vistas](../creating-new-documents-windows-and-views.md) y [Nota técnica 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxstat_. h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Llame a esta función en el `DllMain` de un archivo DLL de extensión de MFC para inicializar el archivo DLL.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Referencia a la estructura de [estructura AFX_EXTENSION_MODULE](afx-extension-module-structure.md) que contendrá el estado del módulo DLL de extensión de MFC después de la inicialización. El estado incluye una copia de los objetos de la clase en tiempo de ejecución que ha inicializado el archivo DLL de extensión de MFC como parte de la construcción del objeto estático normal que se ha ejecutado antes de que se especifique `DllMain`.

*hModule*<br/>
Identificador del módulo DLL de extensión de MFC.

### <a name="return-value"></a>Valor devuelto

TRUE si el archivo DLL de extensión de MFC se ha inicializado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Por ejemplo:

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;
...
```

`AfxInitExtensionModule` realiza una copia de los HMODULE del archivo DLL y captura las clases de tiempo de ejecución (`CRuntimeClass` estructuras) del archivo DLL, así como sus generadores de objetos (objetos`COleObjectFactory`) para su uso posterior cuando se crea el objeto de `CDynLinkLibrary`.
Los archivos dll de extensión de MFC deben hacer dos cosas en su `DllMain` función:

- Llame a [AfxInitExtensionModule](#afxinitextensionmodule) y compruebe el valor devuelto.

- Cree un objeto `CDynLinkLibrary` si el archivo DLL va a exportar objetos de [estructura CRuntimeClass](cruntimeclass-structure.md) o tiene sus propios recursos personalizados.

Puede llamar a `AfxTermExtensionModule` para limpiar el archivo DLL de extensión de MFC cuando cada proceso se desasocie de la DLL de extensión de MFC (lo que sucede cuando se cierra el proceso, o cuando el archivo DLL se descarga como resultado de una llamada `AfxFreeLibrary`).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdll_. h

## <a name="afxsetambientactctx"></a>AfxSetAmbientActCtx

Use esta función para establecer la marca de estado por módulo, que afecta al comportamiento de WinSxS de MFC.

### <a name="syntax"></a>Sintaxis

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parámetros

*bSet*<br/>
Nuevo valor de la marca de estado del módulo.

### <a name="remarks"></a>Observaciones

Cuando se establece la marca (que es el valor predeterminado) y un subproceso entra en un módulo MFC (vea [AFX_MANAGE_STATE](#afx_manage_state)), se activa el contexto del módulo.
Si no se establece la marca, el contexto del módulo no se activa en la entrada.
El contexto de un módulo se determina a partir de su manifiesto, normalmente incrustado en los recursos del módulo.

### <a name="example"></a>Ejemplo

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxcomctl32. h

## <a name="afxtermextensionmodule"></a>AfxTermExtensionModule

Llame a esta función para permitir que MFC Limpie el archivo DLL de extensión de MFC cuando cada proceso se desasocie de la DLL (lo que ocurre cuando se cierra el proceso, o cuando el archivo DLL se descarga como resultado de una llamada `AfxFreeLibrary`).

### <a name="syntax"></a>Sintaxis

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Referencia a la estructura [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) que contiene el estado del módulo DLL de extensión MFC.

*Papeles*<br/>
Si es TRUE, limpie todos los módulos DLL de extensión de MFC. En caso contrario, limpie solo el módulo DLL actual.

### <a name="remarks"></a>Observaciones

`AfxTermExtensionModule` eliminará cualquier almacenamiento local asociado al módulo y quitará todas las entradas de la caché del mapa de mensajes. Por ejemplo:

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

        new CMyDynLinkLibrary(NVC_MFC_DLLDLL);

    }
    else if (dwReason == DLL_PROCESS_DETACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Terminating!\n");

        // Terminate the library before destructors are called
        AfxTermExtensionModule(NVC_MFC_DLLDLL);
    }
    return 1;   // ok
}
```

Si la aplicación carga y libera los archivos dll de extensión de MFC dinámicamente, asegúrese de llamar a `AfxTermExtensionModule`. Dado que la mayoría de los archivos dll de extensión de MFC no se cargan dinámicamente (normalmente, se vinculan a través de las bibliotecas de importación), la llamada a `AfxTermExtensionModule` no suele ser necesaria.

Los archivos dll de extensión de MFC deben llamar a [AfxInitExtensionModule](#afxinitextensionmodule) en su `DllMain`. Si el archivo DLL va a exportar objetos [CRuntimeClass](cruntimeclass-structure.md) o tiene sus propios recursos personalizados, también debe crear un objeto `CDynLinkLibrary` en `DllMain`.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdll_. h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Administración de los datos de estado de los módulos MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
