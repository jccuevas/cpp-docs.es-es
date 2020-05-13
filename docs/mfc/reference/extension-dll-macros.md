---
title: Macros y funciones para administrar archivos DLL
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: 42a08ff2e806acae6713c9df3fe170f7e89f05af
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751599"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Macros y funciones para administrar archivos DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exportaciones de clases.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Proteger una función exportada en un archivo DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Proporciona compatibilidad con OLE desde un archivo DLL de MFC normal que está vinculado dinámicamente a MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Proporciona compatibilidad con sockets MFC desde un archivo DLL de MFC normal que está vinculado dinámicamente a MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Obtiene el estado actual de la marca de estado por módulo.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Establece el estado del módulo antes de la inicialización y/o para restaurar el estado del módulo anterior después de la limpieza.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Inicializa el archivo DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|establecer el indicador de estado por módulo, que afecta al comportamiento de WinSxS de MFC.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Permite a MFC limpiar el archivo DLL de extensión MFC cuando cada proceso se separa del archivo DLL.|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a>AFX_EXT_CLASS

[Los archivos DLL de extensión MFC](../../build/extension-dlls.md) usan la AFX_EXT_CLASS de macro para exportar clases; los ejecutables que se vinculan a la DLL de extensión MFC utilizan la macro para importar clases.

### <a name="remarks"></a>Observaciones

Con la macro AFX_EXT_CLASS, los mismos archivos de encabezado utilizados para compilar el archivo DLL de extensión MFC se pueden utilizar con los ejecutables que se vinculan al archivo DLL.

En el archivo de encabezado del archivo DLL, agregue la palabra clave AFX_EXT_CLASS a la declaración de la clase de la siguiente manera:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Para obtener más información, consulte [Exportar e importar mediante AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxv_dll.h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a>AFX_MANAGE_STATE

Llame a esta macro para proteger una función exportada en un archivo DLL.

### <a name="syntax"></a>Sintaxis

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parámetros

*pModuleState*<br/>
Un puntero `AFX_MODULE_STATE` a una estructura.

### <a name="remarks"></a>Observaciones

Cuando se invoca esta macro, *pModuleState* es el estado de módulo efectivo para el resto del ámbito contenedor inmediato. Al salir del ámbito, el estado del módulo efectivo anterior se restaurará automáticamente.
La `AFX_MODULE_STATE` estructura contiene datos globales para el módulo, es decir, la parte del estado del módulo que se inserta o se extrae.

De forma predeterminada, MFC usa el identificador de recursos de la aplicación principal para cargar la plantilla de recursos. Si tiene una función exportada en un archivo DLL, como una que inicia un cuadro de diálogo en el archivo DLL, esta plantilla se almacena realmente en el módulo DLL. Usted necesita cambiar el estado del módulo para que se utilice el manejador correcto. Puede hacerlo agregando el siguiente código al principio de la función:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Esto intercambia el estado del módulo actual con el estado devuelto desde [AfxGetStaticModuleState](#afxgetstaticmodulestate) hasta el final del ámbito actual.

Para obtener más información sobre los estados de módulo y MFC, vea "Administración de los datos de estado de los módulos MFC" en [Creación de nuevos documentos, windows y vistas](../creating-new-documents-windows-and-views.md) y nota técnica [58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
> Cuando MFC crea un contexto de activación para un ensamblado, `AFX_MANAGE_STATE` usa [AfxWinInit](application-information-and-management.md#afxwininit) para crear el contexto y activarlo y desactivarlo. Tenga en `AFX_MANAGE_STATE` cuenta también que está habilitado para las bibliotecas MFC estáticas, así como los archivos DLL de MFC, con el fin de permitir que el código MFC se ejecute en el contexto de activación adecuado seleccionado por el archivo DLL de usuario. Para obtener más información, vea Compatibilidad con contextos de [activación en el estado del módulo MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxstat_.h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>AfxOleInitModule

Para la compatibilidad con OLE desde un archivo DLL de MFC normal que está `CWinApp::InitInstance` vinculado dinámicamente a MFC, llame a esta función en la función de DLL de MFC normal para inicializar el archivo DLL OLE de MFC.

### <a name="syntax"></a>Sintaxis

```cpp
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Observaciones

El archivo DLL OLE de MFC es un archivo DLL de extensión MFC; para que un archivo DLL de `CDynLinkLibrary` extensión MFC se `CDynLinkLibrary` conectara a una cadena, debe crear un objeto en el contexto de cada módulo que lo usará. `AfxOleInitModule`crea `CDynLinkLibrary` el objeto en el contexto del archivo DLL de `CDynLinkLibrary` MFC normal para que se conecta a la cadena de objetos de la DLL de MFC normal.

Si está creando un control `COleControlModule`OLE y está `AfxOleInitModule` utilizando , no debe llamar porque la `InitInstance` función miembro para `COleControlModule` las llamadas `AfxOleInitModule`.

### <a name="requirements"></a>Requisitos

**Encabezado** \<: afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a>AfxNetInitModule

Para la compatibilidad de sockets MFC desde un archivo DLL de MFC normal que está vinculado `CWinApp::InitInstance` dinámicamente a MFC, agregue una llamada a esta función en la función de DLL de MFC normal para inicializar el archivo DLL de sockets MFC.

### <a name="syntax"></a>Sintaxis

```cpp
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Observaciones

El archivo DLL de sockets MFC es un archivo DLL de extensión MFC; para que un archivo DLL de `CDynLinkLibrary` extensión MFC se `CDynLinkLibrary` conectara a una cadena, debe crear un objeto en el contexto de cada módulo que lo usará. `AfxNetInitModule`crea `CDynLinkLibrary` el objeto en el contexto del archivo DLL de `CDynLinkLibrary` MFC normal para que se conecta a la cadena de objetos de la DLL de MFC normal.

### <a name="requirements"></a>Requisitos

**Encabezado:** \<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a>AfxGetAmbientActCtx

Utilice esta función para obtener el estado actual de la marca de estado por módulo, que afecta al comportamiento de WinSxS de MFC.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del indicador de estado del módulo.

### <a name="remarks"></a>Observaciones

Cuando se establece el indicador (que es el valor predeterminado) y un subproceso entra en un módulo MFC (consulte [AFX_MANAGE_STATE](#afx_manage_state)), se activa el contexto del módulo.

Si no se establece el indicador, el contexto del módulo no se activa en la entrada.

El contexto de un módulo se determina a partir de su manifiesto, normalmente incrustado en los recursos del módulo.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState

Llame a esta función para establecer el estado del módulo antes de la inicialización y/o para restaurar el estado del módulo anterior después de limpiar.

### <a name="syntax"></a>Sintaxis

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Valor devuelto

Un puntero `AFX_MODULE_STATE` a una estructura.

### <a name="remarks"></a>Observaciones

La `AFX_MODULE_STATE` estructura contiene datos globales para el módulo, es decir, la parte del estado del módulo que se inserta o se extrae.

De forma predeterminada, MFC usa el identificador de recursos de la aplicación principal para cargar la plantilla de recursos. Si tiene una función exportada en un archivo DLL, como una que inicia un cuadro de diálogo en el archivo DLL, esta plantilla se almacena realmente en el módulo DLL. Usted necesita cambiar el estado del módulo para que se utilice el manejador correcto. Puede hacerlo agregando el siguiente código al principio de la función:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Esto intercambia el estado actual del `AfxGetStaticModuleState` módulo con el estado devuelto desde el final del ámbito actual.

Para obtener más información sobre los estados de módulo y MFC, vea "Administración de los datos de estado de los módulos MFC" en [Creación de nuevos documentos, windows y vistas](../creating-new-documents-windows-and-views.md) y nota técnica [58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Llame `DllMain` a esta función en un archivo DLL de extensión MFC para inicializar el archivo DLL.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Una referencia a la [estructura de estructura de AFX_EXTENSION_MODULE](afx-extension-module-structure.md) que contendrá el estado del módulo DLL de extensión MFC después de la inicialización. El estado incluye una copia de los objetos de clase en tiempo de ejecución `DllMain` que se han inicializado mediante el archivo DLL de extensión MFC como parte de la construcción normal de objetos estáticos ejecutada antes se especifica.

*hModule*<br/>
Identificador del módulo DLL de extensión MFC.

### <a name="return-value"></a>Valor devuelto

TRUESi el archivo DLL de extensión MFC se inicializa correctamente; de lo contrario, FALSE.

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

`AfxInitExtensionModule`realiza una copia de HMODULE del archivo DLL y captura`CRuntimeClass` las clases en tiempo de`COleObjectFactory` ejecución del archivo `CDynLinkLibrary` DLL (estructuras), así como sus fábricas de objetos (objetos) para su uso más adelante cuando se crea el objeto.
Los archivos DLL de extensión MFC `DllMain` deben hacer dos cosas en su función:

- Llame a [AfxInitExtensionModule](#afxinitextensionmodule) y compruebe el valor devuelto.

- Cree `CDynLinkLibrary` un objeto si el archivo DLL exportará [objetos CRuntimeClass Structure](cruntimeclass-structure.md) o tiene sus propios recursos personalizados.

Puede llamar `AfxTermExtensionModule` para limpiar el archivo DLL de extensión MFC cuando cada proceso se separa del archivo DLL de extensión MFC `AfxFreeLibrary` (que se produce cuando se cierra el proceso, o cuando se descarga el archivo DLL como resultado de una llamada).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdll_.h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a>AfxSetAmbientActCtx

Utilice esta función para establecer el indicador de estado por módulo, que afecta al comportamiento de WinSxS de MFC.

### <a name="syntax"></a>Sintaxis

```cpp
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parámetros

*Bset*<br/>
Nuevo valor del indicador de estado del módulo.

### <a name="remarks"></a>Observaciones

Cuando se establece el indicador (que es el valor predeterminado) y un subproceso entra en un módulo MFC (consulte [AFX_MANAGE_STATE](#afx_manage_state)), se activa el contexto del módulo.
Si no se establece el indicador, el contexto del módulo no se activa en la entrada.
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

**Encabezado:** afxcomctl32.h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a>AfxTermExtensionModule

Llame a esta función para permitir que MFC para limpiar el archivo DLL de extensión MFC cuando cada proceso se desasocia del archivo DLL (lo que ocurre cuando se cierra el proceso, o cuando se descarga el archivo DLL como resultado de una `AfxFreeLibrary` llamada).

### <a name="syntax"></a>Sintaxis

```cpp
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Una referencia a la estructura [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) que contiene el estado del módulo DLL de extensión MFC.

*Bola*<br/>
Si es TRUE, limpie todos los módulos DLL de extensión MFC. De lo contrario, limpie solo el módulo DLL actual.

### <a name="remarks"></a>Observaciones

`AfxTermExtensionModule`eliminará cualquier almacenamiento local adjunto al módulo y eliminará las entradas de la caché del mapa de mensajes. Por ejemplo:

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

Si la aplicación carga y libera archivos DLL de extensión `AfxTermExtensionModule`MFC dinámicamente, asegúrese de llamar a . Puesto que la mayoría de los archivos DLL de extensión MFC no se cargan `AfxTermExtensionModule` dinámicamente (normalmente, están vinculados a través de sus bibliotecas de importación), la llamada a normalmente no es necesaria.

Los archivos DLL de extensión MFC deben llamar `DllMain`a [AfxInitExtensionModule](#afxinitextensionmodule) en su archivo . Si el archivo DLL exportará objetos [CRuntimeClass](cruntimeclass-structure.md) o tiene sus `CDynLinkLibrary` propios `DllMain`recursos personalizados, también debe crear un objeto en .

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdll_.h

## <a name="see-also"></a>Vea también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Administración de los datos de estado de los módulos MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
