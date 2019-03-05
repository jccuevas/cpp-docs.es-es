---
title: Mapas de comandos de edición de DHTML
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 1f84a56876f1108e9b02d44f6ef0dec50f065c57
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278267"
---
# <a name="dhtml-editing-command-maps"></a>Mapas de comandos de edición de DHTML

Se pueden usar las macros siguientes para asignar comandos de edición de DHTML [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-las clases derivadas. Para obtener un ejemplo de su uso, consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Macros de mapa de comandos de edición de DHTML

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Declara una asignación de comandos de edición DHTML en una clase.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Inicia la definición de un mapa de comando de edición de DHTML dentro de una clase.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Marca el final de una asignación de comandos de edición de DHTML.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Asigna un identificador de comando a un comando de edición HTML.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Asigna un identificador de comando a un comando de edición de HTML y el controlador de mensajes.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Asigna un identificador de comando a un comando de edición de HTML y el elemento de la interfaz de usuario.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Asigna un identificador de comando a una elemento de la interfaz de usuario, el controlador de mensajes y comandos de edición de HTML.|

##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP

Declara una asignación de comandos de edición DHTML en una clase.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
Nombre de la clase.

### <a name="remarks"></a>Comentarios

Esta macro es que se usará en la definición de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-las clases derivadas.

Use [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) para implementar la asignación.

### <a name="example"></a>Ejemplo

Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP

Inicia la definición de un mapa de comando de edición de DHTML dentro de una clase.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
El nombre de la clase que contiene la asignación de comandos de edición de DHTML. Esta clase debe derivar directa o indirectamente de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) e incluyen el [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) macro dentro de su definición de clase.

### <a name="remarks"></a>Comentarios

Agregue una asignación de comandos de edición de DHTML a la clase para asignar comandos de la interfaz de usuario a los comandos de edición HTML.

Coloque el begin_dhtmlediting_cmdmap (macro) en el archivo de implementación (.cpp) de la clase seguido [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) macros para los comandos de la clase consiste en asignar (por ejemplo, desde ID_EDIT_CUT a IDM_CUT). Use la [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) macro para marcar el final de la asignación de eventos.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP

Marca el final de una asignación de comandos de edición de DHTML.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Comentarios

Use junto con [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Ejemplo

Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY

Asigna un identificador de comando a un comando de edición HTML.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
El identificador de comando (por ejemplo, ID_EDIT_COPY).

*dhtmlcmdID*<br/>
El comando para que de edición de HTML *cmdID* asigna (por ejemplo, IDM_COPY).

### <a name="example"></a>Ejemplo

Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC

Asigna un identificador de comando a un comando de edición de HTML y el controlador de mensajes.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
El identificador de comando (por ejemplo, ID_EDIT_COPY).

*dhtmlcmdID*<br/>
El comando para que de edición de HTML *cmdID* asigna (por ejemplo, IDM_COPY).

*member_func_name*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="example"></a>Ejemplo

Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE

Asigna un identificador de comando a un comando de edición de HTML y el elemento de la interfaz de usuario.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
El identificador de comando (por ejemplo, ID_EDIT_COPY).

*dhtmlcmdID*<br/>
El comando para que de edición de HTML *cmdID* asigna (por ejemplo, IDM_COPY).

*elemType*<br/>
El tipo de elemento de interfaz de usuario; uno de AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX o AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Ejemplo

Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Asigna un identificador de comando a una elemento de la interfaz de usuario, el controlador de mensajes y comandos de edición de HTML.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
El identificador de comando (por ejemplo, ID_EDIT_COPY).

*dhtmlcmdID*<br/>
El comando para que de edición de HTML *cmdID* asigna (por ejemplo, IDM_COPY).

*member_func_name*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

*elemType*<br/>
El tipo de elemento de interfaz de usuario; uno de AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX o AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Ejemplo

Consulte [ejemplo HTMLEdit](../../visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
