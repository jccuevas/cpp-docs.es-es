---
title: "Mapas de comandos de edición de DHTML | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 89aa66d3a1e85183baaba21f001b60e080895f7f
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="dhtml-editing-command-maps"></a>Mapas de comandos de edición de DHTML
Las macros siguientes se pueden usar para asignar comandos de edición de DHTML [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-las clases derivadas. Para obtener un ejemplo de su uso, consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="dhtml-editing-command-map-macros"></a>Macros de mapa de comandos de edición de DHTML  
  
|||  
|-|-|  
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Declara un mapa de comando de edición de DHTML en una clase.|  
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Inicia la definición de un mapa de comando de edición de DHTML dentro de una clase.|  
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Marca el final de una asignación de comandos de edición de DHTML.|  
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Asigna un identificador de comando a un comando de edición HTML.|  
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Asigna un identificador de comando a un comando de edición de HTML y el controlador de mensajes.|  
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Asigna un identificador de comando a un comando de edición de HTML y el elemento de la interfaz de usuario.|  
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Asigna un identificador de comando a una comando, el controlador de mensajes y el elemento de la interfaz de usuario de edición de HTML.|  
  
##  <a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP  
 Declara un mapa de comando de edición de DHTML en una clase.  
  
```  
DECLARE_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>Parámetros  
 `className`  
 Nombre de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro es que se usará en la definición de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-las clases derivadas.  
  
 Utilice [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) para implementar la asignación.  
  
### <a name="example"></a>Ejemplo  
 Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP  
 Inicia la definición de un mapa de comando de edición de DHTML dentro de una clase.  
  
```  
BEGIN_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>Parámetros  
 `className`  
 El nombre de la clase que contiene la asignación de comandos de edición de DHTML. Esta clase debe derivar directa o indirectamente de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) e incluya el [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) macro dentro de su definición de clase.  
  
### <a name="remarks"></a>Comentarios  
 Agregar un mapa de comando de edición de DHTML a la clase para asignar comandos de la interfaz de usuario a los comandos de edición HTML.  
  
 Colocar el `BEGIN_DHTMLEDITING_CMDMAP` seguido de macro en el archivo de implementación (.cpp) de la clase [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) macros para los comandos de la clase es asignar (por ejemplo, de **ID_EDIT_CUT** a **IDM_CUT**). Utilice la [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) macro para marcar el final de la asignación de eventos.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP  
 Marca el final de una asignación de comandos de edición de DHTML.  
  
```  
END_DHTMLEDITING_CMDMAP()   
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice junto con [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).  
  
### <a name="example"></a>Ejemplo  
 Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY  
 Asigna un identificador de comando a un comando de edición HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)   
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 El identificador de comando (como **ID_EDIT_COPY**).  
  
 `dhtmlcmdID`  
 El comando para que de edición de HTML `cmdID` asigna (como **IDM_COPY**).  
  
### <a name="example"></a>Ejemplo  
 Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC  
 Asigna un identificador de comando a un comando de edición de HTML y el controlador de mensajes.  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 El identificador de comando (como **ID_EDIT_COPY**).  
  
 `dhtmlcmdID`  
 El comando para que de edición de HTML `cmdID` asigna (como **IDM_COPY**).  
  
 `member_func_name`  
 El nombre de la función de controlador de mensajes al que está asignado el comando.  
  
### <a name="example"></a>Ejemplo  
 Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE  
 Asigna un identificador de comando a un comando de edición de HTML y el elemento de la interfaz de usuario.  
  
```  
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)  
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 El identificador de comando (como **ID_EDIT_COPY**).  
  
 `dhtmlcmdID`  
 El comando para que de edición de HTML `cmdID` asigna (como **IDM_COPY**).  
  
 `elemType`  
 El tipo de elemento de interfaz de usuario; uno de **AFX_UI_ELEMTYPE_NORMAL**, **AFX_UI_ELEMTYPE_CHECKBOX**, o **AFX_UI_ELEMTYPE_RADIO**.  
  
### <a name="example"></a>Ejemplo  
 Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE  
 Asigna un identificador de comando a una comando, el controlador de mensajes y el elemento de la interfaz de usuario de edición de HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)   
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 El identificador de comando (como **ID_EDIT_COPY**).  
  
 `dhtmlcmdID`  
 El comando para que de edición de HTML `cmdID` asigna (como **IDM_COPY**).  
  
 `member_func_name`  
 El nombre de la función de controlador de mensajes al que está asignado el comando.  
  
 `elemType`  
 El tipo de elemento de interfaz de usuario; uno de **AFX_UI_ELEMTYPE_NORMAL**, **AFX_UI_ELEMTYPE_CHECKBOX**, o **AFX_UI_ELEMTYPE_RADIO**.  
  
### <a name="example"></a>Ejemplo  
 Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

