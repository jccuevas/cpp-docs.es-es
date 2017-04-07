---
title: Macros de mapa (MFC) de mensajes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- message map macros
- Windows messages [C++], declaration
- demarcating Windows messages
- message maps [C++], macros
- message maps [C++], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
caps.latest.revision: 10
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
ms.sourcegitcommit: d4b97ed874b145f9c6d9a9536476243bba0fd1c1
ms.openlocfilehash: 0c5856dce919ca8ea2d396fbf2523dc45409b519
ms.lasthandoff: 03/06/2017

---
# <a name="message-map-macros-mfc"></a>Macros de mapa de mensajes (MFC)
Para admitir los mapas de mensajes, MFC proporciona las siguientes macros:  
  
### <a name="message-map-declaration-and-demarcation-macros"></a>Declaración de mapa de mensajes y Macros de demarcación  
  
|||  
|-|-|  
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Declara que se utilizará un mapa de mensajes en una clase para asignar mensajes a funciones (utilizado en la declaración de clase).|  
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Inicia la definición de un mapa de mensajes (debe utilizarse en la implementación de la clase).|  
|[END_MESSAGE_MAP](#end_message_map)|Termina la definición de un mapa de mensajes (debe utilizarse en la implementación de la clase).|  
  
### <a name="message-mapping-macros"></a>Macros de asignación de mensajes  
  
|||  
|-|-|  
|[ON_COMMAND](#on_command)|Indica qué función controlará un mensaje de comando especificado.|  
|[ON_CONTROL](#on_control)|Indica qué función controlará un mensaje de notificación de control especificado.|  
|[ON_MESSAGE](#on_message)|Indica qué función controlará un mensaje definido por el usuario.|  
|[ON_OLECMD](#on_olecmd)|Indica qué función controlará un comando de menú de DocObject o su contenedor.|  
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Indica qué función controlará un mensaje definido por el usuario registrado.|  
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Indica la función que controlará un mensaje definido por el usuario registrado cuando tiene un `CWinThread` clase.|  
|[ON_THREAD_MESSAGE](#on_thread_message)|Indica la función que controlará un mensaje definido por el usuario cuando tiene un `CWinThread` clase.|  
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Indica qué función controlará un mensaje de comando de actualización de interfaz de usuario especificado.|  
  
### <a name="message-map-range-macros"></a>Macros de mapa de mensajes intervalo  
  
|||  
|-|-|  
|[ON_COMMAND_RANGE](#on_command_range)|Indica qué función va a controlar el intervalo de identificadores de comando especificados en los dos primeros parámetros a la macro.|  
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Indica qué controlador de actualización va a controlar el intervalo de identificadores de comando especificados en los dos primeros pa] Pará a la macro.|  
|[ON_CONTROL_RANGE](#on_control_range)|Indica la función que controlará las notificaciones desde el intervalo de identificadores especificados en los parámetros segundo y terceros a la macro de control. El primer parámetro es un mensaje de notificación de control, como **BN_CLICKED**.|  
  
 Para obtener más información sobre los mapas de mensajes, la declaración de mapa de mensajes y macros de delimitación y las macros de asignación de mensajes, consulte [mapas de mensajes](../../mfc/reference/message-maps-mfc.md) y [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md). Para obtener más información acerca de los intervalos de mapa de mensajes, consulte [controladores para intervalos de mapa de mensajes de](../../mfc/handlers-for-message-map-ranges.md).  

## <a name="declare_message_map"></a>DECLARE_MESSAGE_MAP
 Declara que la clase define un mapa de mensajes. Cada `CCmdTarget`-clase derivada en el programa debe proporcionar un mapa de mensajes para controlar los mensajes.  
  
### <a name="syntax"></a>Sintaxis  
  
```    
DECLARE_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `DECLARE_MESSAGE_MAP` macro al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones de miembro para la clase, use la `BEGIN_MESSAGE_MAP` (macro), las entradas de macro para cada una de las funciones de controlador de mensajes y el `END_MESSAGE_MAP` (macro).  
  
> [!NOTE]
>  Si se declara ningún miembro después `DECLARE_MESSAGE_MAP`, debe especificar un nuevo tipo de acceso (**público**, `private`, o `protected`) para ellos.  
  
 Para obtener más información sobre el mensaje se asigna y la `DECLARE_MESSAGE_MAP` (macro), consulte [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Ejemplo  
```cpp  
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
``` 
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  

## <a name="begin_message_map"></a>BEGIN_MESSAGE_MAP
Inicia la definición de su mapa de mensajes.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
BEGIN_MESSAGE_MAP( theClass, baseClass )  
```  
  
### <a name="parameters"></a>Parámetros  
 `theClass`  
 Especifica el nombre de la clase cuyo mensaje asignar todo esto.  
  
 `baseClass`  
 Especifica el nombre de la clase base de `theClass`.  
  
### <a name="remarks"></a>Comentarios  
 En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, iniciar el mapa de mensajes con el `BEGIN_MESSAGE_MAP` (macro), a continuación, agregue entradas de macro para cada una de las funciones de controlador de mensajes y completar el mapa de mensajes con el `END_MESSAGE_MAP` (macro).  
  
 Para obtener más información acerca de los mapas de mensajes, consulte [mapas de mensajes](message-maps-mfc.md)  
  
### <a name="example"></a>Ejemplo  
```cpp  
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h 

## <a name="end_message_map"></a>END_MESSAGE_MAP
Termina la definición de su mapa de mensajes.  
  
### <a name="syntax"></a>Sintaxis  
  
```   
END_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el mensaje se asigna y la `END_MESSAGE_MAP` (macro), consulte [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  

## <a name="on_command"></a>ON_COMMAND
Esta macro asigna un mensaje de comando a una función miembro.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_COMMAND( id, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 Identificador del comando.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes al que está asignado el comando.  
  
### <a name="remarks"></a>Comentarios  
 Indica qué función controlará un mensaje de comando de un objeto de interfaz de usuario de comando como un botón de barra de herramientas o el elemento de menú.  
  
 Cuando un objeto de destino del comando recibe un Windows **WM_COMMAND** mensaje con el identificador especificado, `ON_COMMAND` llamará a la función miembro `memberFxn` para controlar el mensaje.  
  
 Utilice `ON_COMMAND` para asignar un único comando a una función miembro. Utilice [ON_COMMAND_RANGE](#on_command_range) para asignar un intervalo de identificadores de comando a un miembro de función. Sólo una entrada de mapa de mensajes puede coincidir con un identificador de comando especificado. Es decir, no puede asignar un comando a más de un controlador. Para obtener más información y ejemplos, vea [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Ejemplo  
```cpp  
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
``` 
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmsg_.h  
  
## <a name="on_control"></a>ON_CONTROL
Indica qué función controlará un mensaje de notificación de control personalizado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_CONTROL( wNotifyCode, id, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `wNotifyCode`  
 El código de notificación del control.  
  
 `id`  
 Identificador del comando.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes al que está asignado el comando.  
  
### <a name="remarks"></a>Comentarios  
 Mensajes de notificación de control son aquellos enviados desde un control a su ventana primaria.  
  
 Debe haber exactamente un `ON_CONTROL` instrucción de macro en el mapa de mensajes para cada mensaje de notificación de control que se debe asignar a una función de controlador de mensajes.  
  
 Para obtener más información y ejemplos, vea [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmsg_.h  
  

## <a name="on_message"></a>ON_MESSAGE  
Indica qué función controlará un mensaje definido por el usuario.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `message`  
 El id. del mensaje.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes al que está asignado el mensaje.  
  
 El tipo de la función debe ser `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.  
  
### <a name="remarks"></a>Comentarios  
 Mensajes definidos por el usuario son los mensajes que no son estándar de Windows `WM_MESSAGE` mensajes. Al seleccionar un identificador de mensaje, debe utilizar valores dentro del intervalo de `WM_USER` (0 x 0400) que 0x7FFF o `WM_APP` (0 x 8000) a 0xBFFF. Para obtener más información sobre identificadores de mensaje, consulte [WM_APP](http://msdn.microsoft.com/library/windows/desktop/ms644930).  
  
 Debe haber exactamente un `ON_MESSAGE` instrucción de macro en el mapa de mensajes para cada mensaje definido por el usuario que se debe asignar a una función de controlador de mensajes.  
  
> [!NOTE]
>  Además de los mensajes definidos por el usuario, `ON_MESSAGE` controla los mensajes de Windows menos comunes. Para obtener más información, consulte el artículo de Knowledge Base [99848: INFO: Use ON_MESSAGE() Macro mapa menos comunes mensajes](http://go.microsoft.com/fwlink/?linkId=192022).  
  
 Para obtener más información y ejemplos, vea [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md) y [controladores definidos por el usuario](user-defined-handlers.md)  
  
### <a name="example"></a>Ejemplo  
```cpp  
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
 afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

 LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here. 

   return 0;
}
```   
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmsg_.h  

## <a name="on_olecmd"></a>ON_OLECMD    
Enruta los comandos a través de la interfaz de envío del comando `IOleCommandTarget`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_OLECMD( pguid, olecmdid, id )  
```  
  
### <a name="parameters"></a>Parámetros  
 `pguid`  
 Identificador del grupo de comandos a la que pertenece el comando. Utilice **NULL** para el grupo estándar.  
  
 *olecmdid*  
 El identificador del comando OLE.  
  
 `id`  
 El identificador de menú, Id. de la barra de herramientas, identificador de botón u otro Id. del recurso o del objeto que se emite el comando.  
  
### <a name="remarks"></a>Comentarios  
 `IOleCommandTarget`permite a un contenedor recibir comandos originados en la interfaz de usuario del DocObject y permite al contenedor enviar los mismos comandos (como nuevo, abrir, guardar como e imprimir en el menú archivo; y copiar, pegar, deshacer, etc., en el menú Edición) para DocObject.  
  
 `IOleCommandTarget`es más sencillo que la de automatización OLE `IDispatch`. `IOleCommandTarget`se basa completamente en un conjunto estándar de comandos que no suelen tener argumentos y no implicada ninguna información de tipo (seguridad de tipos se reduce para argumentos del comando). Si necesita enviar comandos con argumentos, utilice [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).  
  
 El `IOleCommandTarget` comandos de menú estándar se han implementado por MFC en las macros siguientes:  
  
 **(DE ON_OLECMD_CLEARSELECTION)**  
  
 Envía el comando Editar Clear. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`  
  
 **(DE ON_OLECMD_COPY)**  
  
 Envía el comando Editar una copia. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`  
  
 **(DE ON_OLECMD_CUT)**  
  
 Envía el comando Editar Cortar. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`  
  
 **(DE ON_OLECMD_NEW)**  
  
 Envía el comando nuevo archivo. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`  
  
 **(DE ON_OLECMD_OPEN)**  
  
 Envía el comando Abrir archivo. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`  
  
 **(DE ON_OLECMD_PAGESETUP)**  
  
 Envía el comando Configurar página de archivo. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`  
  
 **(DE ON_OLECMD_PASTE)**  
  
 Envía el comando Pegar. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`  
  
 **(DE ON_OLECMD_PASTESPECIAL)**  
  
 Envía el comando Editar Pegado especial. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`  
  
 **(DE ON_OLECMD_PRINT)**  
  
 Envía el comando Imprimir del archivo. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`  
  
 **(DE ON_OLECMD_PRINTPREVIEW)**  
  
 Envía el comando de vista previa de impresión de archivos. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`  
  
 **(DE ON_OLECMD_REDO)**  
  
 Envía el comando Editar rehacer. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`  
  
 **(DE ON_OLECMD_SAVE)**  
  
 Envía el comando Guardar archivo. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`  
  
 **(DE ON_OLECMD_SAVE_AS)**  
  
 Envía el comando Guardar como. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`  
  
 **(DE ON_OLECMD_SAVE_COPY_AS)**  
  
 Envía el comando Guardar copia como. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`  
  
 **(DE ON_OLECMD_SELECTALL)**  
  
 Envía el comando Editar Seleccionar todo. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`  
  
 **(DE ON_OLECMD_UNDO)**  
  
 Envía el comando Deshacer Editar. Se implementa como:  
  
 `ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdocob.h  
  
### <a name="see-also"></a>Vea también  
 [Clase COleCmdUI](colecmdui-class.md)   
 [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)

## <a name="on_registered_message"></a>ON_REGISTERED_MESSAGE
Windows **RegisterWindowMessage** función se utiliza para definir un nuevo mensaje de ventana que se garantiza que sea único en todo el sistema.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `nMessageVariable`  
 La variable de Id. de mensaje registrado de ventana.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes al que está asignado el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro indica qué función tratará el mensaje registrado.  
  
 Para obtener más información y ejemplos, vea [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Ejemplo  
```cpp  
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));


BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmsg_.h  
  
### <a name="see-also"></a>Vea también  
 [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)   
 [Controladores definidos por el usuario](user-defined-handlers.md)

## <a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE    
Indica la función que controlará el mensaje registrado por la función RegisterWindowMessage de Windows.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `nMessageVariable`  
 La variable de Id. de mensaje registrado de ventana.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes de CWinThread al que está asignado el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 RegisterWindowMessage se utiliza para definir un nuevo mensaje de ventana que se garantiza que sea único en todo el sistema. ON_REGISTERED_THREAD_MESSAGE debe utilizarse en lugar de ON_REGISTERED_MESSAGE cuando tiene una clase de CWinThread. 
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmsg_.h  

## <a name="on_thread_message"></a>ON_THREAD_MESSAGE    
Indica qué función controlará un mensaje definido por el usuario.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_THREAD_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `message`  
 El id. del mensaje.  
  
 `memberFxn`  
 El nombre de la `CWinThread`-message-función de controlador al que está asignado el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 `ON_THREAD_MESSAGE`debe usarse en lugar de `ON_MESSAGE` cuando haya un `CWinThread` clase. Mensajes definidos por el usuario son los mensajes que no son estándar de Windows **WM_MESSAGE** mensajes. Debe haber exactamente un `ON_THREAD_MESSAGE` instrucción de macro en el mapa de mensajes para cada mensaje definido por el usuario que se debe asignar a una función de controlador de mensajes.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  

## <a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI    
Esta macro indica qué función controlará un mensaje de comando de actualización de interfaz de usuario.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_UPDATE_COMMAND_UI( id, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 El id. del mensaje.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes al que está asignado el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Debe haber exactamente un `ON_UPDATE_COMMAND_UI` instrucción de macro en el mapa de mensajes para cada comando de actualización de la interfaz de usuario que se debe asignar a una función de controlador de mensajes.  
  
 Para obtener más información y ejemplos, vea [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
### <a name="see-also"></a>Vea también  
 [CCmdUI (clase)](ccmdui-class.md)

## <a name="on_command_range"></a>ON_COMMAND_RANGE  
Use esta macro para asignar un intervalo contiguo de identificadores de comando a una función de controlador de mensaje único.  
  
### <a name="syntax"></a>Sintaxis
  
```  
ON_COMMAND_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `id1`  
 Id. de comando al principio de un intervalo contiguo de identificadores de comando.  
  
 `id2`  
 Id. de comando al final de un intervalo contiguo de identificadores de comando.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes a los que se asignan los comandos.  
  
### <a name="remarks"></a>Comentarios  
 El intervalo de identificadores comienza con `id1` y termina con `id2`.  
  
 Utilice `ON_COMMAND_RANGE` para asignar un intervalo de identificadores de comando a un miembro de función. Utilice [ON_COMMAND](#on_command) para asignar un único comando a una función miembro. Sólo una entrada de mapa de mensajes puede coincidir con un Id. Es decir, no puede asignar un comando a más de un controlador. Para obtener más información sobre los rangos de asignación de mensajes, consulte [controladores para intervalos de mapa de mensajes de](../../mfc/handlers-for-message-map-ranges.md).  
  
 No hay ninguna compatibilidad automática de intervalos de mapa de mensajes, por lo que debe colocar la macro.  
  
### <a name="example"></a>Ejemplo  
```cpp  
// The code fragment below shows how to use ON_COMMAND_RANGE macro 
// to map a contiguous range of command IDs to a single message  
// handler function (i.e. OnRangeCmds() in the sample below). In  
// addition, it also shows how to use CheckMenuRadioItem() to check a  
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, 
      nID, MF_BYCOMMAND);
}
```
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmsg_.h  

## <a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE    
Asigna un intervalo contiguo de identificadores de comando a una función de controlador de mensaje de actualización individual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `id1`  
 Id. de comando al principio de un intervalo contiguo de identificadores de comando.  
  
 `id2`  
 Id. de comando al final de un intervalo contiguo de identificadores de comando.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes de actualización al que se asignan los comandos.  
  
### <a name="remarks"></a>Comentarios  
 Controladores de mensajes de actualización de actualización el estado de los elementos de menú y botones de barra de herramientas asociado al comando. El intervalo de identificadores comienza con `id1` y termina con `id2`.  
  
 No hay ninguna compatibilidad automática de intervalos de mapa de mensajes, por lo que debe colocar la macro.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmsg_.h  

## <a name="on_control_range"></a>ON_CONTROL_RANGE     
Utilice esta macro para asignar un intervalo contiguo de identificadores de control a una función de controlador de mensaje único para un mensaje de notificación de Windows especificado, como **BN_CLICKED**.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parámetros  
 `wNotifyCode`  
 El código de notificación al que está respondiendo al controlador.  
  
 `id1`  
 Id. de comando al principio de un intervalo contiguo de identificadores de control.  
  
 `id2`  
 Id. de comando al final de un intervalo contiguo de identificadores de control.  
  
 `memberFxn`  
 El nombre de la función de controlador de mensajes a los que se asignan a los controles.  
  
### <a name="remarks"></a>Comentarios  
 El intervalo de identificadores comienza con `id1` y termina con `id2`. Se llama al controlador para la notificación especificada procedentes de cualquiera de los controles asignados.  
  
 No hay ninguna compatibilidad automática de intervalos de mapa de mensajes, por lo que debe colocar la macro.  
  
 Para obtener más información sobre cómo implementar funciones de controlador para un intervalo de identificadores de control, consulte [controladores para intervalos de mapa de mensajes de](../../mfc/handlers-for-message-map-ranges.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmsg_.h  
  



