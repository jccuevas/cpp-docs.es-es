---
title: Mapas de comandos de edición de DHTML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d040f3cb4c9bf8e1f3afc0e8213cd4513fc8571
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123375"
---
# <a name="dhtml-editing-command-maps"></a>Mapas de comandos de edición de DHTML
Las macros siguientes se pueden usar para asignar comandos de edición de DHTML [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-las clases derivadas. Para obtener un ejemplo de su uso, consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="dhtml-editing-command-map-macros"></a>Macros de mapa de comandos de edición de DHTML  
  
|||  
|-|-|  
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Declara una asignación de comandos de edición de DHTML en una clase.|  
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Inicia la definición de un mapa de comando de edición de DHTML dentro de una clase.|  
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Marca el final de una asignación de comandos de edición de DHTML.|  
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Asigna un identificador de comando a un comando de edición de HTML.|  
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Asigna un identificador de comando a un comando de edición de HTML y el controlador de mensajes.|  
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Asigna un identificador de comando a un comando de edición de HTML y el elemento de la interfaz de usuario.|  
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Asigna un identificador de comando a una comando, el controlador de mensajes y el elemento de la interfaz de usuario de edición de HTML.|  
  
##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP  
 Declara una asignación de comandos de edición de DHTML en una clase.  
  
```  
DECLARE_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>Parámetros  
 *nombre de clase*  
 Nombre de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro es que se usará en la definición de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-las clases derivadas.  
  
 Use [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) para implementar la asignación.  
  
### <a name="example"></a>Ejemplo  
 Vea [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP  
 Inicia la definición de un mapa de comando de edición de DHTML dentro de una clase.  
  
```  
BEGIN_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>Parámetros  
 *nombre de clase*  
 El nombre de la clase que contiene la asignación de comandos de edición de DHTML. Esta clase debe derivar directa o indirectamente de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) e incluya el [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) macro dentro de su definición de clase.  
  
### <a name="remarks"></a>Comentarios  
 Agregue una asignación de comandos de edición de DHTML a la clase para asignar comandos de la interfaz de usuario a los comandos de edición HTML.  
  
 Coloque el BEGIN_DHTMLEDITING_CMDMAP (macro) en el archivo de implementación (.cpp) de la clase seguido [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) macros para los comandos de la clase consiste en crear una asignación (por ejemplo, de ID_EDIT_CUT a IDM_CUT). Use la [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) macro para marcar el final de la asignación de eventos.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP  
 Marca el final de una asignación de comandos de edición de DHTML.  
  
```  
END_DHTMLEDITING_CMDMAP()   
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice junto con [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).  
  
### <a name="example"></a>Ejemplo  
 Vea [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY  
 Asigna un identificador de comando a un comando de edición de HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)   
```  
  
### <a name="parameters"></a>Parámetros  
 *cmdID*  
 El identificador de comando (por ejemplo, ID_EDIT_COPY).  
  
 *dhtmlcmdID*  
 El código HTML modificar (comando) a la que *cmdID* asigna (por ejemplo, IDM_COPY).  
  
### <a name="example"></a>Ejemplo  
 Vea [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC  
 Asigna un identificador de comando a un comando de edición de HTML y el controlador de mensajes.  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *cmdID*  
 El identificador de comando (por ejemplo, ID_EDIT_COPY).  
  
 *dhtmlcmdID*  
 El código HTML modificar (comando) a la que *cmdID* asigna (por ejemplo, IDM_COPY).  
  
 *member_func_name*  
 El nombre de la función de controlador de mensajes al que está asignado el comando.  
  
### <a name="example"></a>Ejemplo  
 Vea [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE  
 Asigna un identificador de comando a un comando de edición de HTML y el elemento de la interfaz de usuario.  
  
```  
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)  
```  
  
### <a name="parameters"></a>Parámetros  
 *cmdID*  
 El identificador de comando (por ejemplo, ID_EDIT_COPY).  
  
 *dhtmlcmdID*  
 El código HTML modificar (comando) a la que *cmdID* asigna (por ejemplo, IDM_COPY).  
  
 *elemType*  
 El tipo de elemento de interfaz de usuario; uno de AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX o AFX_UI_ELEMTYPE_RADIO.  
  
### <a name="example"></a>Ejemplo  
 Vea [ejemplo HTMLEdit](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE  
 Asigna un identificador de comando a una comando, el controlador de mensajes y el elemento de la interfaz de usuario de edición de HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)   
```  
  
### <a name="parameters"></a>Parámetros  
 *cmdID*  
 El identificador de comando (por ejemplo, ID_EDIT_COPY).  
  
 *dhtmlcmdID*  
 El código HTML modificar (comando) a la que *cmdID* asigna (por ejemplo, IDM_COPY).  
  
 *member_func_name*  
 El nombre de la función de controlador de mensajes al que está asignado el comando.  
  
 *elemType*  
 El tipo de elemento de interfaz de usuario; uno de AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX o AFX_UI_ELEMTYPE_RADIO.  
  
### <a name="example"></a>Ejemplo  
 Vea [ejemplo HTMLEdit](../../visual-cpp-samples.md).  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxhtml.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
