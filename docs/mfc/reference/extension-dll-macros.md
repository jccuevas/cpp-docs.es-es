---
title: Macros y funciones para administrar los archivos DLL | Microsoft Docs
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426e23aa935cd0b0add664c1eeb3885181cb4e6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383758"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Macros y funciones para administrar los archivos DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exporta las clases.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Proteger una función exportada en un archivo DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Proporciona compatibilidad con OLE de DLL MFC estándar que se vincule dinámicamente a MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Proporciona compatibilidad con Sockets de MFC desde una DLL de MFC normal que se vincule dinámicamente a MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Obtiene el estado actual de la marca de estado por módulo.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Establece el estado del módulo antes de la inicialización o para restaurar el estado del módulo anterior después de la limpieza.|
|[AfxInitExtensionModule]()#afxinitextensionmodule|Inicializa el archivo DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|Establezca el indicador de estado por módulo, lo que afecta al comportamiento de WinSxS de MFC.|
|[AfxTermExtensionModule]()#afxtermextensionmodule)|Permite MFC limpiar el archivo DLL de extensión MFC cuando se separa cada proceso en el archivo DLL.|


## <a name="afx_ext_class"></a>  AFX_EXT_CLASS

[DLL de extensión MFC](../../build/extension-dlls.md) utilice la macro AFX_EXT_CLASS para exportar clases; los archivos ejecutables que se vinculan a la DLL de extensión MFC utilizan la macro para importar las clases.

### <a name="remarks"></a>Comentarios

AFX_EXT_CLASS (macro), se pueden utilizar los mismos archivos de encabezado utilizados para generar el archivo DLL de extensión MFC con los archivos ejecutables que vinculen a la DLL.

En el archivo de encabezado para el archivo DLL, agregue la palabra clave AFX_EXT_CLASS a la declaración de la clase:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Para obtener más información, consulte [exportar e importar utilizando AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Requisitos

Encabezado: **afxv_** dll.h

## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE

Llame a esta macro para proteger una función exportada en un archivo DLL.

### <a name="syntax"></a>Sintaxis

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```
### <a name="parameters"></a>Parámetros

*pModuleState*<br/>
Un puntero a un `AFX_MODULE_STATE` estructura.

### <a name="remarks"></a>Comentarios

Cuando se invoca esta macro, *pModuleState* es el estado efectivo del módulo para el resto de la inmediata ámbito contenedor. Al salir del ámbito, se restaurará automáticamente el estado efectivo del módulo anterior.
El `AFX_MODULE_STATE` estructura contiene los datos globales del módulo, es decir, la parte del estado del módulo que se insertaron o se extraen.
De forma predeterminada, MFC utiliza el identificador de recurso de la aplicación principal para cargar la plantilla de recursos. Si tiene una función exportada en un archivo DLL, como el que se abre un cuadro de diálogo en el archivo DLL, esta plantilla se almacena realmente en el módulo DLL. Deberá cambiar el estado del módulo para el identificador correcto que se usará. Puede hacerlo agregando el código siguiente al principio de la función:
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
Esto cambia el estado actual del módulo con el estado devuelto desde [AfxGetStaticModuleState](#afxgetstaticmodulestate) hasta el final del ámbito actual.
Para obtener más información sobre los Estados de módulos y MFC, vea "Administrar el estado de datos de los módulos MFC" en [crear nuevos documentos, Windows y las vistas](../creating-new-documents-windows-and-views.md) y [Nota técnica 58](../tn058-mfc-module-state-implementation.md).
> [!NOTE]
>  Cuando MFC crea un contexto de activación de un ensamblado, utiliza [AfxWinInit](#afxwininit) para crear el contexto y `AFX_MANAGE_STATE` para activar y desactivar. Tenga en cuenta también que `AFX_MANAGE_STATE` está habilitada para que estático bibliotecas MFC, así como archivos DLL de MFC, con el fin de permitir que el código MFC ejecutar en el contexto de activación correcto seleccionado por el archivo DLL de usuario. Para obtener más información, consulte [compatibilidad con contextos de activación en el estado del módulo MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).
### <a name="requirements"></a>Requisitos

**Encabezado:** afxstat_.h

### <a name="see-also"></a>Vea también

[AfxGetStaticModuleState](#afxgetstaticmodulestate)

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

Para obtener soporte de DLL MFC estándar que se vincule dinámicamente a MFC OLE, llame a esta función en su MFC DLL regular `CWinApp::InitInstance` esa función para inicializar la DLL MFC OLE.

### <a name="syntax"></a>Sintaxis

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Comentarios

La DLL MFC OLE es una extensión MFC DLL; para una DLL de extensión MFC que puedan obtener conectados con un `CDynLinkLibrary` cadena, debe crear un `CDynLinkLibrary` objeto en el contexto de cada módulo que lo va a usar. `AfxOleInitModule` crea el `CDynLinkLibrary` objeto en contexto de su MFC DLL regular para que se obtiene con cable en el `CDynLinkLibrary` objeto de cadena de la DLL de MFC regular.

Si está creando un control OLE y usas `COleControlModule`, no debe llamar a `AfxOleInitModule` porque el `InitInstance` función miembro para `COleControlModule` llamadas `AfxOleInitModule`.

### <a name="requirements"></a>Requisitos

**Encabezado**: \<afxdll_.h >

### <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxnetinitmodule"></a>  AfxNetInitModule

Para admitir Sockets de MFC desde una DLL de MFC normal que se vincule dinámicamente a MFC, agregue una llamada a esta función en su MFC DLL regular `CWinApp::InitInstance` esa función para inicializar el archivo DLL de Sockets de MFC.

### <a name="syntax"></a>Sintaxis

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Comentarios

La DLL de Sockets de MFC es una extensión MFC DLL; para una DLL de extensión MFC que puedan obtener conectados con un `CDynLinkLibrary` cadena, debe crear un `CDynLinkLibrary` objeto en el contexto de cada módulo que lo va a usar. `AfxNetInitModule` crea el `CDynLinkLibrary` objeto en contexto de su MFC DLL regular para que se obtiene con cable en el `CDynLinkLibrary` objeto de cadena de la DLL de MFC regular.

### <a name="requirements"></a>Requisitos

**Encabezado:** \<afxdll_.h >

### <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxgetambientactctx"></a> AfxGetAmbientActCtx

Utilice esta función para obtener el estado actual de la marca de estado por módulo, que afecta al comportamiento de WinSxS de MFC.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del módulo estado marca.

### <a name="remarks"></a>Comentarios

Cuando se establece la marca (que es el valor predeterminado) y un subproceso entra en un módulo MFC (vea [AFX_MANAGE_STATE](#afx_manage_state)), se activa el contexto del módulo.

Si no se establece la marca, el contexto del módulo no está activado en la entrada.

El contexto de un módulo se determina a partir de su manifiesto, que normalmente se incrustan en los recursos del módulo.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxcomctl32.h

### <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[AFX_MANAGE_STATE](#afx_manage_state)<br/>
[Administración de los datos de estado de los módulos MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
[AfxSetAmbientActCtx](#setambientactctx)

## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState

Llame a esta función para establecer el estado del módulo antes de la inicialización o para restaurar el estado del módulo anterior después de la limpieza.

### <a name="syntax"></a>Sintaxis

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un `AFX_MODULE_STATE` estructura.

### <a name="remarks"></a>Comentarios

El `AFX_MODULE_STATE` estructura contiene los datos globales del módulo, es decir, la parte del estado del módulo que se insertaron o se extraen.

De forma predeterminada, MFC utiliza el identificador de recurso de la aplicación principal para cargar la plantilla de recursos. Si tiene una función exportada en un archivo DLL, como el que se abre un cuadro de diálogo en el archivo DLL, esta plantilla se almacena realmente en el módulo DLL. Deberá cambiar el estado del módulo para el identificador correcto que se usará. Puede hacerlo agregando el código siguiente al principio de la función:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```

Esto cambia el estado actual del módulo con el estado devuelto desde `AfxGetStaticModuleState` hasta el final del ámbito actual.

Para obtener más información sobre los Estados de módulos y MFC, vea "Administrar el estado de datos de los módulos MFC" en [crear nuevos documentos, Windows y las vistas](../creating-new-documents-windows-and-views.md) y [Nota técnica 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxstat_.h


## <a name="afxinitextensionmodule"></a> AfxInitExtensionModule

Llame a esta función en una DLL de extensión MFC `DllMain` para inicializar el archivo DLL.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```
### <a name="parameters"></a>Parámetros

*state*<br/>
Una referencia a la [AFX_EXTENSION_MODULE (estructura)](afx-extension-module-structure.md) estructura que contiene el estado del módulo DLL de extensión MFC después de la inicialización. El estado incluye una copia de los objetos de clase en tiempo de ejecución que se hayan inicializado por el archivo DLL de extensión MFC como parte de la construcción del objeto estático normal ejecutada antes de `DllMain` se ha especificado.

*hModule*<br/>
Identificador del módulo DLL de extensión MFC.

### <a name="return-value"></a>Valor devuelto

TRUE si el archivo DLL de extensión MFC se inicializó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

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

```

`AfxInitExtensionModule` realiza una copia de HMODULE la DLL y clases en tiempo de ejecución de la DLL de captura (`CRuntimeClass` estructuras), así como los generadores de objetos (`COleObjectFactory` objetos) para su uso posterior cuando la `CDynLinkLibrary` se crea el objeto.
Extensión MFC DLL necesario hacer dos cosas en sus `DllMain` función:
- Llame a [AfxInitExtensionModule](#_mfc_afxinitextensionmodule) y compruebe el valor devuelto.
- Crear un `CDynLinkLibrary` objeto si va a exportar el archivo DLL [CRuntimeClass (estructura)](cruntimeclass-structure.md) objetos o tiene sus propios recursos personalizados.
Puede llamar a `AfxTermExtensionModule` para limpiar el archivo DLL de extensión MFC cuando cada proceso se separa de la DLL de extensión MFC (lo que ocurre cuando se cierra el proceso, o cuando se descarga el archivo DLL como resultado de una `AfxFreeLibrary` llamar).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdll_.h

### <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[AfxTermExtensionModule](#afxtermextensionmodule)

## <a name="afxsetambientactctx"></a>  AfxSetAmbientActCtx

Utilice esta función para establecer la marca de estado por módulo, que afecta al comportamiento de WinSxS de MFC.

### <a name="syntax"></a>Sintaxis

  ```
   void AFXAPI AfxSetAmbientActCtx( BOOL bSet
);
```
### <a name="parameters"></a>Parámetros

*bSet*<br/>
Nuevo valor de la marca de estado de módulo.

### <a name="remarks"></a>Comentarios

Cuando se establece la marca (que es el valor predeterminado) y un subproceso entra en un módulo MFC (vea [AFX_MANAGE_STATE](#afx_manage_state)), se activa el contexto del módulo.
Si no se establece la marca, el contexto del módulo no está activado en la entrada.
El contexto de un módulo se determina a partir de su manifiesto, que normalmente se incrustan en los recursos del módulo.

### <a name="example"></a>Ejemplo

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxcomctl32.h

### <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[AfxGetAmbientActCtx](#afxgetambientactctx)<br/>
[AFX_MANAGE_STATE](#afx_manage_state)<br/>
[Administración de los datos de estado de los módulos MFC](../managing-the-state-data-of-mfc-modules.md)

## <a name="afxtermextensionmodule"></a>  AfxTermExtensionModule

Llame a esta función para permitir MFC para realizar la limpieza del archivo DLL de extensión MFC cuando se separa cada proceso en el archivo DLL (lo que ocurre cuando se cierra el proceso, o cuando se descarga el archivo DLL como resultado de una `AfxFreeLibrary` llamar).

### <a name="syntax"></a>Sintaxis

  ```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```
### <a name="parameters"></a>Parámetros

*state*<br/>
Una referencia a la [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) estructura que contiene el estado del módulo DLL de extensión MFC.

*Bola*<br/>
Si es TRUE, limpiar todos los módulos DLL de extensión MFC. Limpieza en caso contrario, solo el módulo DLL actual.

### <a name="remarks"></a>Comentarios

`AfxTermExtensionModule` eliminará cualquier almacenamiento local conectado al módulo y quitar todas las entradas de la caché del mapa de mensajes. Por ejemplo:

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

Si la aplicación se carga y libera la DLL de extensión MFC dinámicamente, no olvide llamar a `AfxTermExtensionModule`. Desde la mayoría de extensión de MFC archivos DLL no se cargaron dinámicamente (por lo general, están vinculadas a través de sus bibliotecas de importación), la llamada a `AfxTermExtensionModule` normalmente no es necesario.

Extensión de MFC DLL debe llamar a [AfxInitExtensionModule](#afxinitextensionmodule) en sus `DllMain`. Si va a exportar el archivo DLL [CRuntimeClass](cruntimeclass-structure.md) objetos o tiene sus propios recursos personalizados, también deberá crear un `CDynLinkLibrary` objeto `DllMain`.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdll_.h

### <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[AfxInitExtensionModule](#afxinitextensionmodule)





