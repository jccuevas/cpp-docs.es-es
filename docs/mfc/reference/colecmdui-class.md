---
title: Clase COleCmdUI | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
dev_langs:
- C++
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e6195735c25bb188449638750f6100869a44f082
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370762"
---
# <a name="colecmdui-class"></a>Clase COleCmdUI
Implementa un método para que MFC actualice el estado de los objetos relacionados con características de la aplicación orientadas a `IOleCommandTarget`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleCmdUI::COleCmdUI](#colecmdui)|Construye un objeto `COleCmdUI`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleCmdUI::Enable](#enable)|Establece o borra la marca de comando enable.|  
|[COleCmdUI::SetCheck](#setcheck)|Establece el estado de un comando alternante activado/desactivado comando.|  
|[COleCmdUI::SetText](#settext)|Devuelve una cadena de texto Nombre o el estado de un comando.|  
  
## <a name="remarks"></a>Comentarios  
 En una aplicación que no está habilitada para DocObjects, cuando el usuario ve un menú en la aplicación, procesos MFC **UPDATE_COMMAND_UI** notificaciones. Cada notificación recibe un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto que se puede manipular para reflejar el estado de un comando concreto. Sin embargo, cuando la aplicación está habilitada para DocObjects, MFC procesa **UPDATE_OLE_COMMAND_UI** notificaciones y asigna `COleCmdUI` objetos.  
  
 `COleCmdUI` permite un DocObject pueda recibir comandos que se originan en la interfaz de usuario de su contenedor (por ejemplo, FileNew, abrir, impresión etc.), y un contenedor recibir comandos que se originan en la interfaz de usuario del DocObject. Aunque `IDispatch` podría utilizarse para distribuir los mismos comandos, `IOleCommandTarget` proporciona una manera más sencilla de consultar y ejecutar porque se basa en un conjunto estándar de comandos, normalmente sin argumentos, y no está implicada ninguna información de tipo. `COleCmdUI` puede usarse para habilitar, actualizar y establecer otras propiedades de DocObject comandos de la interfaz de usuario. Cuando desea invocar el comando, llame a [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).  
  
 Para obtener más información sobre DocObjects, consulte [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md). Consulte también [primeros pasos de Internet: documentos activos](../../mfc/active-documents-on-the-internet.md) y [documentos activos](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdocobj.h  
  
##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI  
 Construye un `COleCmdUI` objeto asociado a un comando de la interfaz de usuario concreta.  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>Parámetros  
 `rgCmds`  
 Una lista de los comandos admitidos asociados con el GUID especificado. El **OLECMD** estructura asocia comandos con marcadores de comando.  
  
 *cCmds*  
 El número de comandos de `rgCmds`.  
  
 `pGroup`  
 Un puntero a un GUID que identifica un conjunto de comandos.  
  
### <a name="remarks"></a>Comentarios  
 La `COleCmdUI` objeto proporciona una interfaz de programación para actualizar los objetos de interfaz de usuario de DocObject como botones de barra de controles o elementos de menú. Los objetos de interfaz de usuario se pueden habilitados, deshabilitados, activados o desactivados a través de la `COleCmdUI` objeto.  
  
##  <a name="enable"></a>  COleCmdUI::Enable  
 Llame a esta función para establecer el indicador de comando de la `COleCmdUI` el objeto a **OLECOMDF_ENABLED**, lo que indica la interfaz, el comando está disponible y habilitada, o para borrar el indicador de comando.  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>Parámetros  
 `bOn`  
 Indica si el comando asociado a la `COleCmdUI` objeto debe habilitarse o deshabilitarse. NonZero habilita el comando; 0 deshabilita el comando.  
  
##  <a name="setcheck"></a>  COleCmdUI::SetCheck  
 Llame a esta función para establecer el estado de un comando alternante activado/desactivado comando.  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCheck`  
 Un valor que determina el estado para establecer una alternancia activado/desactivado comando. Los valores son:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**1**|El comando se establece en on.|  
|**2**|Establece el comando a indeterminado; no se puede determinar el estado porque el atributo de este comando es en y fuera de Estados de la selección pertinente.|  
|Cualquier otro valor|Establece el comando en off.|  
  
##  <a name="settext"></a>  COleCmdUI::SetText  
 Llame a esta función para devolver una cadena de texto Nombre o el estado de un comando.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Un puntero al texto que se utilizará con el comando.  
  
## <a name="see-also"></a>Vea también  
 [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



