---
title: Clase COleCmdUI | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- document object server
- COleCmdUI class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
caps.latest.revision: 21
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 38e7019d7636166262028d955455cee675824f8b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="colecmdui-class"></a>Clase COleCmdUI
Implementa un método para que MFC actualice el estado de los objetos relacionados con características de la aplicación orientadas a `IOleCommandTarget`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleCmdUI::COleCmdUI](#colecmdui)|Construye un objeto `COleCmdUI`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleCmdUI::Enable](#enable)|Establece o borra el indicador de comando enable.|  
|[COleCmdUI::SetCheck](#setcheck)|Establece el estado de un botón de alternancia o desactivar comando.|  
|[COleCmdUI::SetText](#settext)|Devuelve una cadena de texto de nombre o el estado de un comando.|  
  
## <a name="remarks"></a>Comentarios  
 En una aplicación que no está habilitada para DocObjects, cuando el usuario ve un menú en la aplicación, procesos MFC **UPDATE_COMMAND_UI** notificaciones. Cada tipo de notificación un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto que se puede manipular para reflejar el estado de un comando determinado. Sin embargo, cuando la aplicación está habilitada para DocObjects, MFC procesa **UPDATE_OLE_COMMAND_UI** notificaciones y asigna `COleCmdUI` objetos.  
  
 `COleCmdUI`permite un DocObject pueda recibir comandos originados en la interfaz de usuario de su contenedor (como ArchivoNuevo, abrir, imprimir y así sucesivamente), y un contenedor recibir comandos originados en la interfaz de usuario del DocObject. Aunque `IDispatch` podría utilizarse para enviar los mismos comandos, `IOleCommandTarget` proporciona una forma más sencilla de consultar y ejecutar porque depende de un conjunto estándar de comandos, normalmente sin argumentos, y no está implicada ninguna información de tipo. `COleCmdUI`puede utilizarse para habilitar, actualizar y establecer otras propiedades de los comandos de interfaz de usuario de DocObject. Cuando desea invocar el comando, llame a [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).  
  
 Para obtener más información sobre DocObjects, consulte [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md). Consulte también [primeros pasos de Internet: documentos activos](../../mfc/active-documents-on-the-internet.md) y [documentos activos](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdocobj.h  
  
##  <a name="colecmdui"></a>COleCmdUI::COleCmdUI  
 Construye un `COleCmdUI` objeto asociado a un comando de la interfaz de usuario concreta.  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>Parámetros  
 `rgCmds`  
 Una lista de los comandos admitidos asociados con el GUID especificado. El **OLECMD** estructura asocia comandos con indicadores de comando.  
  
 *cCmds*  
 El número de comandos de `rgCmds`.  
  
 `pGroup`  
 Puntero a un GUID que identifica un conjunto de comandos.  
  
### <a name="remarks"></a>Comentarios  
 La `COleCmdUI` objeto proporciona una interfaz de programación para actualizar objetos de interfaz de usuario de DocObject como elementos de menú o botones de barra de control. Los objetos de interfaz de usuario se pueden habilitados, deshabilitados, activados o desactivados a través de la `COleCmdUI` objeto.  
  
##  <a name="enable"></a>COleCmdUI::Enable  
 Llame a esta función para establecer el indicador de comando de la `COleCmdUI` objeto **OLECOMDF_ENABLED**, que indica la interfaz con el comando está disponible y habilitada, o para borrar el indicador de comando.  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>Parámetros  
 `bOn`  
 Indica si el comando asociado con el `COleCmdUI` objeto debe estar habilitado o deshabilitado. NonZero habilita el comando; 0 deshabilita el comando.  
  
##  <a name="setcheck"></a>COleCmdUI::SetCheck  
 Llame a esta función para establecer el estado de un botón de alternancia o desactivar comando.  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCheck`  
 Un valor que determina el estado que se establece una alternancia de encendido y apagado comando. Los valores son:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**1**|El comando se establece en on.|  
|**2**|Establece el comando para indeterminado; no se puede determinar el estado porque el atributo de este comando está en y fuera de los Estados de la selección correspondiente.|  
|cualquier otro valor|Establece el comando en off.|  
  
##  <a name="settext"></a>COleCmdUI::SetText  
 Llame a esta función para devolver una cadena de texto de nombre o el estado de un comando.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Puntero al texto que se usará con el comando.  
  
## <a name="see-also"></a>Vea también  
 [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




