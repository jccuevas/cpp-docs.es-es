---
title: Mapas de comandos de edición de DHTML
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 62b388eb178be018655ea2b2be00d7321da50335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365818"
---
# <a name="dhtml-editing-command-maps"></a>Mapas de comandos de edición de DHTML

Las siguientes macros se pueden utilizar para asignar comandos de edición DHTML en [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-clases derivadas. Para obtener un ejemplo de su uso, vea Ejemplo de [HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Macros de mapa de comandos de edición DHTML

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Declara un mapa de comandos de edición DHTML en una clase.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Inicia la definición de un mapa de comandos de edición DHTML dentro de una clase.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Marca el final de un mapa de comandos de edición DHTML.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Asigna un identificador de comando a un comando de edición HTML.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Asigna un identificador de comando a un comando de edición HTML y un controlador de mensajes.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Asigna un identificador de comando a un comando de edición HTML y un elemento de interfaz de usuario.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Asigna un identificador de comando a un comando de edición HTML, controlador de mensajes y elemento de interfaz de usuario.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP

Declara un mapa de comandos de edición DHTML en una clase.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
Nombre de la clase.

### <a name="remarks"></a>Observaciones

Esta macro se va a utilizar en la definición de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-clases derivadas.

Utilice [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) para implementar el mapa.

### <a name="example"></a>Ejemplo

Consulte [Ejemplo de HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP

Inicia la definición de un mapa de comandos de edición DHTML dentro de una clase.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parámetros

*className*<br/>
El nombre de la clase que contiene el mapa de comandos de edición DHTML. Esta clase debe derivar directa o indirectamente de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) e incluir el [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) macro dentro de su definición de clase.

### <a name="remarks"></a>Observaciones

Agregue un mapa de comandos de edición DHTML a la clase para asignar comandos de interfaz de usuario a comandos de edición HTML.

Coloque la macro BEGIN_DHTMLEDITING_CMDMAP en el archivo de implementación de la clase (.cpp) seguido de [macros DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) para los comandos que la clase debe asignar (por ejemplo, de ID_EDIT_CUT a IDM_CUT). Utilice la macro [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) para marcar el final del mapa de eventos.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP

Marca el final de un mapa de comandos de edición DHTML.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Observaciones

Utilícelo junto con [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Ejemplo

Consulte [Ejemplo de HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY

Asigna un identificador de comando a un comando de edición HTML.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
El ID de comando (como ID_EDIT_COPY).

*dhtmlcmdID*<br/>
El comando de edición HTML al que se asigna *cmdID* (por ejemplo, IDM_COPY).

### <a name="example"></a>Ejemplo

Consulte [Ejemplo de HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC

Asigna un identificador de comando a un comando de edición HTML y un controlador de mensajes.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
El ID de comando (como ID_EDIT_COPY).

*dhtmlcmdID*<br/>
El comando de edición HTML al que se asigna *cmdID* (por ejemplo, IDM_COPY).

*member_func_name*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="example"></a>Ejemplo

Consulte [Ejemplo de HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE

Asigna un identificador de comando a un comando de edición HTML y un elemento de interfaz de usuario.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
El ID de comando (como ID_EDIT_COPY).

*dhtmlcmdID*<br/>
El comando de edición HTML al que se asigna *cmdID* (por ejemplo, IDM_COPY).

*elemType*<br/>
El tipo de elemento de interfaz de usuario; uno de AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX o AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Ejemplo

Consulte [Ejemplo de HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Asigna un identificador de comando a un comando de edición HTML, controlador de mensajes y elemento de interfaz de usuario.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
El ID de comando (como ID_EDIT_COPY).

*dhtmlcmdID*<br/>
El comando de edición HTML al que se asigna *cmdID* (por ejemplo, IDM_COPY).

*member_func_name*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

*elemType*<br/>
El tipo de elemento de interfaz de usuario; uno de AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX o AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Ejemplo

Consulte [Ejemplo de HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxhtml.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
