---
title: Clase CDockState | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
dev_langs:
- C++
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6669f5a2b54c376e545b1ba6b9227d6137726256
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdockstate-class"></a>Clase CDockState
Una clase serializada `CObject` que carga, descarga o desactiva el estado de una o más barras de control de acoplamiento en memoria persistente (un archivo).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDockState : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockState::Clear](#clear)|Borra la información de estado de acoplamiento.|  
|[CDockState::GetVersion](#getversion)|Recupera el número de versión de la suma de comprobación barra de estado.|  
|[CDockState::LoadState](#loadstate)|Recupera información del registro de estado o. Archivo INI.|  
|[CDockState::SaveState](#savestate)|Guarda información de estado en el registro o el archivo INI.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Matriz de punteros a la suma de comprobación se acopla con una entrada para cada barra de controles de información de estado.|  
  
## <a name="remarks"></a>Comentarios  
 El estado de acoplamiento incluye el tamaño y la posición de la barra y si no se acopla. Al recuperar la suma de comprobación acoplar estado, `CDockState` comprueba la barra de la posición y, si no está visible con la configuración de pantalla actual, la barra de `CDockState` escala de la barra de posición para que esté visible. El propósito principal de `CDockState` es para mantener el estado completo de una serie de barras de control y para permitir que ese estado se guarden y cargado en del registro, la aplicación. El archivo INI, o en formato binario como parte de una `CArchive` contenido del objeto.  
  
 La barra puede ser cualquier control acoplable barras, incluida una barra de herramientas, la barra de estado o la barra de cuadro de diálogo. `CDockState`objetos se escriben y leen hacia o desde un archivo a través de un `CArchive` objeto.  
  
 [CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) recupera la información de estado de todas la ventana de marco `CControlBar` objetos y lo coloca en el `CDockState` objeto. A continuación, puede escribir el contenido de la `CDockState` objeto en el almacenamiento con [Serialize](../../mfc/reference/cobject-class.md#serialize) o [CDockState::SaveState](#savestate). Si posteriormente desea restaurar el estado de las barras de control en la ventana de marco, puede cargar el estado con `Serialize` o [CDockState::LoadState](#loadstate), a continuación, utilice [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) para aplicar el guardado estado de barras de control de la ventana de marco.  
  
 Para obtener más información sobre las barras de control de acoplamiento, vea los artículos [barras de Control](../../mfc/control-bars.md), [las barras de herramientas: acoplar y desacoplar](../../mfc/docking-and-floating-toolbars.md), y [ventanas de marco](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxadv.h  
  
##  <a name="clear"></a>CDockState::Clear  
 Llame a esta función para borrar toda la información de acoplamiento almacenada en la `CDockState` objeto.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 Esto incluye no solo si la barra está acoplada o no, pero el tamaño y la posición de la barra y si no está visible.  
  
##  <a name="getversion"></a>CDockState::GetVersion  
 Llame a esta función para recuperar el número de versión de la suma de comprobación barra de estado.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Valor devuelto  
 1 si la barra almacenada información es anterior a la actual de la barra de estado; 2 si la barra almacenada información es el mismo que el actual estado de la barra.  
  
### <a name="remarks"></a>Comentarios  
 Compatibilidad de versiones permite una barra revisada agregar nuevas propiedades persistentes y seguir siendo capaces de detectar y cargar el estado persistente creado por una versión anterior de la barra.  
  
##  <a name="loadstate"></a>CDockState::LoadState  
 Llame a esta función para recuperar información de estado desde el registro o. Archivo INI.  
  
```  
void LoadState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszProfileName`  
 Apunta a una cadena teminated null que especifica el nombre de una sección en el archivo de inicialización o una clave en el registro de Windows donde se almacena información de estado.  
  
### <a name="remarks"></a>Comentarios  
 El nombre del perfil es la sección de la aplicación. INI o el registro que contiene información de estado de las barras. Puede guardar el control de barra de información de estado en el registro o. El archivo INI con `SaveState`.  
  
##  <a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo  
 A `CPtrArray` objeto que es una matriz de punteros a la información de la barra de control almacenado para cada barra de controles que se guarda la información de estado en la `CDockState` objeto.  
  
```  
CPtrArray m_arrBarInfo;  
```  
  
##  <a name="savestate"></a>CDockState::SaveState  
 Llame a esta función para guardar la información de estado en el registro o. Archivo INI.  
  
```  
void SaveState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszProfileName`  
 Apunta a una cadena teminated null que especifica el nombre de una sección en el archivo de inicialización o una clave en el registro de Windows donde se almacena información de estado.  
  
### <a name="remarks"></a>Comentarios  
 El nombre del perfil es la sección de la aplicación. El registro o del archivo INI que contiene información de estado de la barra de control. `SaveState`También guarda el tamaño de pantalla actual. Puede recuperar información de la barra de control del registro o. El archivo INI con `LoadState`.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

