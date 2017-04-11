---
title: "Macros y funciones para la administración de archivos DLL | Documentos de Microsoft"
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: b943ef8dd652df061965fe81ecc9c08115636141
ms.openlocfilehash: fcce68789c18b23a6779278fa7f256a756522764
ms.lasthandoff: 04/04/2017

---
# <a name="macros-and-functions-for-managing-dlls"></a>Macros y funciones para la administración de archivos DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Clases de exportaciones.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Proteger una función exportada en un archivo DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Proporciona compatibilidad con OLE desde un archivo DLL estándar vinculado dinámicamente a MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Proporciona compatibilidad con Sockets de MFC desde un archivo DLL estándar vinculado dinámicamente a MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Obtiene el estado actual de la marca de estado de cada módulo.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Establece el estado del módulo antes de la inicialización o para restaurar el estado del módulo anterior después de la limpieza.|
|[AfxInitExtensionModule]()#afxinitextensionmodule|Inicializa el archivo DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|Establezca el indicador de estado por módulo, que afecta al comportamiento de WinSxS de MFC.|
|[AfxTermExtensionModule]()#afxtermextensionmodule)|Permite MFC limpiar el archivo DLL de extensión cuando se desasocie cada proceso en el archivo DLL.|


## <a name="afx_ext_class"></a>AFX_EXT_CLASS
[Archivos DLL de extensión](../../build/extension-dlls.md) , use la macro **AFX_EXT_CLASS** para exportar clases; los archivos ejecutables que se vinculan a la DLL de extensión utilizan la macro para importar las clases.  
   
### <a name="remarks"></a>Comentarios  
 Con el **AFX_EXT_CLASS** (macro), el mismo encabezado de los archivos que se utilizan para generar el archivo DLL de extensión se pueden utilizar con los archivos ejecutables que se vinculan al archivo DLL.  
  
 En el archivo de encabezado para el archivo DLL, agregue el **AFX_EXT_CLASS** palabra clave a la declaración de la clase como sigue:  
  
```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
``` 
  
 Para obtener más información, consulte [exportar e importar utilizando AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).  
   
### <a name="requirements"></a>Requisitos  
 Encabezado: **afxv_**dll.h  
   
## <a name="afx_manage_state"></a>AFX_MANAGE_STATE
Llame a esta macro para proteger una función exportada en un archivo DLL.  
   
### <a name="syntax"></a>Sintaxis    
```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )  
```
### <a name="parameters"></a>Parámetros  
 `pModuleState`  
 Un puntero a un `AFX_MODULE_STATE` estructura.  
   
### <a name="remarks"></a>Comentarios  
 Cuando se invoca esta macro, `pModuleState` es el estado efectivo del módulo para el resto de la inmediata ámbito contenedor. Al salir del ámbito, se restaurará automáticamente el estado efectivo del módulo anterior.    
 El `AFX_MODULE_STATE` estructura contiene datos globales del módulo, es decir, la parte del estado de módulo que se insertan o se han extraído.    
 De forma predeterminada, MFC usa el identificador de recurso de la aplicación principal para cargar la plantilla de recursos. Si tiene una función exportada en un archivo DLL, como uno que se abre un cuadro de diálogo en el archivo DLL, esta plantilla se almacena realmente en el módulo de archivo DLL. Debe cambiar el estado del módulo para el identificador correcto que se usará. Puede hacerlo agregando el código siguiente al principio de la función:    
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
 Con ello intercambia el estado actual del módulo con el estado devuelto desde [AfxGetStaticModuleState](#afxgetstaticmodulestate) hasta el final del ámbito actual.    
 Para obtener más información sobre los Estados de módulos y MFC, vea "Administrar el estado de datos de los módulos MFC" en [crear nuevos documentos, ventanas y vistas](../creating-new-documents-windows-and-views.md) y [Nota técnica 58](../tn058-mfc-module-state-implementation.md).    
> [!NOTE]
>  Cuando MFC crea un contexto de activación para un ensamblado, utiliza [AfxWinInit](#afxwininit) para crear el contexto y `AFX_MANAGE_STATE` para activar y desactivar. Tenga en cuenta también que `AFX_MANAGE_STATE` está habilitada para que estático bibliotecas MFC, así como archivos DLL de MFC, con el fin de permitir que el código MFC ejecutar en el contexto de activación correcta seleccionado por el archivo DLL de usuario. Para obtener más información, consulte [compatibilidad con contextos de activación en el estado del módulo MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).     
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxstat_.h  
   
### <a name="see-also"></a>Vea también  
 [AfxGetStaticModuleState](#afxgetstaticmodulestate)

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>AfxOleInitModule
Para compatibilidad con OLE desde un archivo DLL estándar vinculado dinámicamente a MFC, llame a esta función en el archivo DLL estándar `CWinApp::InitInstance` función para inicializar la DLL MFC OLE.  
   
### <a name="syntax"></a>Sintaxis    
```
void AFXAPI AfxOleInitModule( );  
```  
   
### <a name="remarks"></a>Comentarios  
 La DLL MFC OLE es una extensión de archivo DLL; en orden para un archivo DLL de extensión para poder conectar a un **CDynLinkLibrary** cadena, debe crear un **CDynLinkLibrary** objeto en el contexto de cada módulo que lo va a usar. `AfxOleInitModule`crea el **CDynLinkLibrary** objeto en el contexto de los DLL normales para que se obtiene con cable en el **CDynLinkLibrary** objeto de cadena de la DLL normal.  
  
 Si está generando un control OLE y utiliza `COleControlModule`, no debería llamar a **AfxOleInitModule** porque el `InitInstance` función de miembro para `COleControlModule` llamadas `AfxOleInitModule`.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado**:<afxdll_.h></afxdll_.h>  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxnetinitmodule"></a>AfxNetInitModule
Por compatibilidad con Sockets de MFC desde un archivo DLL estándar vinculado dinámicamente a MFC, agregue una llamada a esta función en el archivo DLL estándar **CWinApp:: InitInstance** función para inicializar el archivo DLL de Sockets de MFC.  
   
### <a name="syntax"></a>Sintaxis    
```
void AFXAPI AfxNetInitModule( );  
```  
   
### <a name="remarks"></a>Comentarios  
 La DLL de Sockets de MFC es una extensión de archivo DLL; en orden para un archivo DLL de extensión para poder conectar a un **CDynLinkLibrary** cadena, debe crear un **CDynLinkLibrary** objeto en el contexto de cada módulo que lo va a usar. `AfxNetInitModule`crea el **CDynLinkLibrary** objeto en el contexto de los DLL normales para que se obtiene con cable en el **CDynLinkLibrary** objeto de cadena de la DLL normal.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:**<afxdll_.h></afxdll_.h>  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxgetambientactctx"></a>AfxGetAmbientActCtx
Utilice esta función para obtener el estado actual de la marca de estado por módulo, que afecta al comportamiento de WinSxS de MFC.  
   
### <a name="syntax"></a>Sintaxis    
```  
BOOL AFXAPI AfxGetAmbientActCtx();   
```  
   
### <a name="return-value"></a>Valor devuelto  
 Valor actual del módulo estado marca.  
   
### <a name="remarks"></a>Comentarios  
 Cuando se establece la marca (que es el valor predeterminado) y un subproceso entra en un módulo MFC (vea [AFX_MANAGE_STATE](#afx_manage_state)), se activa el contexto del módulo.  
  
 Si no se estableció el marcador, el contexto del módulo no está activado en la entrada.  
  
 El contexto de un módulo se determina a partir de su manifiesto, que normalmente se incrustan en recursos del módulo.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcomctl32.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [Administrar los datos de estado de los módulos MFC](../managing-the-state-data-of-mfc-modules.md)   
 [AfxSetAmbientActCtx](#setambientactctx)
 
## <a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState
Llame a esta función para establecer el estado del módulo antes de la inicialización o para restaurar el estado del módulo anterior después de la limpieza.  
   
### <a name="syntax"></a>Sintaxis    
```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );  
```  
   
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `AFX_MODULE_STATE` estructura.  
   
### <a name="remarks"></a>Comentarios  
 El `AFX_MODULE_STATE` estructura contiene datos globales del módulo, es decir, la parte del estado de módulo que se insertan o se han extraído.  
  
 De forma predeterminada, MFC usa el identificador de recurso de la aplicación principal para cargar la plantilla de recursos. Si tiene una función exportada en un archivo DLL, como uno que se abre un cuadro de diálogo en el archivo DLL, esta plantilla se almacena realmente en el módulo de archivo DLL. Debe cambiar el estado del módulo para el identificador correcto que se usará. Puede hacerlo agregando el código siguiente al principio de la función:  
  
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
  
 Con ello intercambia el estado actual del módulo con el estado devuelto desde `AfxGetStaticModuleState` hasta el final del ámbito actual.  
  
 Para obtener más información sobre los Estados de módulos y MFC, vea "Administrar el estado de datos de los módulos MFC" en [crear nuevos documentos, ventanas y vistas](../creating-new-documents-windows-and-views.md) y [Nota técnica 58](../tn058-mfc-module-state-implementation.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxstat_.h  
   

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule
Llame a esta función en un archivo DLL de extensión `DllMain` para inicializar el archivo DLL.  
   
### <a name="syntax"></a>Sintaxis    
```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );  
```
### <a name="parameters"></a>Parámetros  
 `state`  
 Una referencia a la [AFX_EXTENSION_MODULE (estructura)](afx-extension-module-structure.md) estructura que contiene el estado del módulo de archivo DLL de extensión después de la inicialización. El estado incluye una copia de los objetos de clase en tiempo de ejecución que se ha inicializado por el archivo DLL de extensión como parte de la construcción del objeto estático normal ejecutada antes de `DllMain` se escribe.  
  
 `hModule`  
 Identificador del módulo de archivo DLL de extensión.  
   
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el archivo DLL de extensión está correctamente inicializado; de lo contrario, **FALSE**.  
   
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

        // Extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

```
  
 `AfxInitExtensionModule`realiza una copia de la DLL **HMODULE** y clases en tiempo de ejecución de los archivos DLL de captura (`CRuntimeClass` estructuras), así como los generadores de objetos (`COleObjectFactory` objetos) para su uso posterior cuando el **CDynLinkLibrary** se crea el objeto.    
 Extensión de MFC DLL necesario hacer dos cosas en sus `DllMain` función:    
-   Llame a [AfxInitExtensionModule](#_mfc_afxinitextensionmodule) y compruebe el valor devuelto.   
-   Crear un **CDynLinkLibrary** si va a exportar el archivo DLL del objeto [CRuntimeClass estructura](cruntimeclass-structure.md) objetos o tiene sus propios recursos personalizados.    
 Puede llamar a `AfxTermExtensionModule` para limpiar el archivo DLL de extensión cuando se desasocie cada proceso desde el archivo DLL de extensión (que se produce cuando termina el proceso, o cuando se descarga el archivo DLL como resultado de una `AfxFreeLibrary` llamadas).     

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdll_.h     

### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [AfxTermExtensionModule](#afxtermextensionmodule)

 ## <a name="afxsetambientactctx"></a>AfxSetAmbientActCtx
Utilice esta función para establecer el indicador de estado por módulo, que afecta al comportamiento de WinSxS de MFC.  
   
### <a name="syntax"></a>Sintaxis  
  ```
   void AFXAPI AfxSetAmbientActCtx( BOOL bSet  
);  
```
### <a name="parameters"></a>Parámetros  
 `bSet`  
 Nuevo valor de la marca de estado de módulo.  
   
### <a name="remarks"></a>Comentarios  
 Cuando se establece la marca (que es el valor predeterminado) y un subproceso entra en un módulo MFC (vea [AFX_MANAGE_STATE](#afx_manage_state)), se activa el contexto del módulo.    
 Si no se estableció el marcador, el contexto del módulo no está activado en la entrada.    
 El contexto de un módulo se determina a partir de su manifiesto, que normalmente se incrustan en recursos del módulo.  
   
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
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [AfxGetAmbientActCtx](#afxgetambientactctx)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [Administración de los datos de estado de los módulos MFC](../managing-the-state-data-of-mfc-modules.md) 

## <a name="afxtermextensionmodule"></a>AfxTermExtensionModule

Llame a esta función para permitir MFC para realizar la limpieza del archivo DLL de extensión cuando se desasocie cada proceso en el archivo DLL (que se produce cuando termina el proceso, o cuando se descarga el archivo DLL como resultado de una `AfxFreeLibrary` llamadas).  
   
### <a name="syntax"></a>Sintaxis  
  ```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );  
```
### <a name="parameters"></a>Parámetros  
 `state`  
 Una referencia a la [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) estructura que contiene el estado del módulo de archivo DLL de extensión.  
  
 *Bola*  
 Si **TRUE**, limpiar todos los módulos DLL de extensión. Limpieza en caso contrario, solo el módulo DLL actual.  
   
### <a name="remarks"></a>Comentarios  
 `AfxTermExtensionModule`eliminará cualquier almacenamiento local conectado al módulo y quitar todas las entradas de la caché del mapa de mensajes. Por ejemplo:  
  
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

        // Extension DLL one-time initialization
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
  
 Si la aplicación se carga y libera dinámicamente los archivos DLL de extensión, no olvide llamar `AfxTermExtensionModule`. Desde la mayoría de extensión DLL no se cargan dinámicamente (por lo general, se vinculan a través de sus bibliotecas de importación), la llamada a `AfxTermExtensionModule` normalmente no es necesario.  
  
 Archivos DLL de extensión MFC necesitan llamar a [AfxInitExtensionModule](#afxinitextensionmodule) en sus `DllMain`. Si va a exportar el archivo DLL [CRuntimeClass](cruntimeclass-structure.md) objetos o tiene sus propios recursos personalizados, también debe crear un **CDynLinkLibrary** objeto `DllMain`.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdll_.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [AfxInitExtensionModule](#afxinitextensionmodule)
 





