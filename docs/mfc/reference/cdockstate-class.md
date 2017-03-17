---
title: Clase CDockState | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
- dock state
- size
- docking control bars
- CDockState class
- states, dockable control bar
- position, control bar
- size, control bar
- docking tool windows
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: fc8beb80cc35c1816fbc305ece2bfbc5df2e7cd0
ms.lasthandoff: 02/24/2017

---
# <a name="cdockstate-class"></a>Clase CDockState
Una clase serializada `CObject` que carga, descarga o desactiva el estado de una o más barras de control de acoplamiento en memoria persistente (un archivo).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDockState : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockState::Clear](#clear)|Borra la información de estado de acoplamiento.|  
|[CDockState::GetVersion](#getversion)|Recupera el número de versión de los datos almacenados en la barra de estado.|  
|[CDockState::LoadState](#loadstate)|Recupera información de estado desde el registro o. Archivo INI.|  
|[CDockState::SaveState](#savestate)|Guarda información de estado en el registro o el archivo INI.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Matriz de punteros a almacenado acopla la información de estado con una entrada para cada barra de control.|  
  
## <a name="remarks"></a>Comentarios  
 El estado de acoplamiento incluye el tamaño y posición de la barra y si no está acoplado. Al recuperar almacenado acoplar el estado, `CDockState` comprueba la barra de la posición y, si no está visible con la configuración de pantalla actual, la barra de `CDockState` escala de la barra de posición para que sea visible. El propósito principal de `CDockState` es para mantener el estado completo de una serie de barras de control y para permitir que se guarda el estado y cargarse en del registro, la aplicación. Archivo INI, o en formato binario como parte de una `CArchive` contenido del objeto.  
  
 La barra puede ser cualquier control acoplable barras, incluida una barra de herramientas, la barra de estado o la barra de cuadro de diálogo. `CDockState`los objetos se escriben y se leen a o desde un archivo a través de un `CArchive` objeto.  
  
 [CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) recupera la información de estado de todos los fotogramas de la ventana `CControlBar` objetos y lo coloca en el `CDockState` objeto. A continuación, puede escribir el contenido de la `CDockState` objeto de almacenamiento con [Serialize](../../mfc/reference/cobject-class.md#serialize) o [CDockState::SaveState](#savestate). Si más adelante desea restaurar el estado de las barras de control en la ventana de marco, puede cargar el estado con `Serialize` o [CDockState::LoadState](#loadstate), a continuación, utilice [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) para aplicar el estado guardado a barras de control de la ventana de marco.  
  
 Para obtener más información sobre las barras de control de acoplamiento, consulte los artículos [barras de Control](../../mfc/control-bars.md), [las barras de herramientas: acoplar y desacoplar](../../mfc/docking-and-floating-toolbars.md), y [ventanas de marco](../../mfc/frame-windows.md).  
  
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
 Esto incluye no sólo si la barra se acopla o no, pero el tamaño y la posición de la barra y si es visible o no.  
  
##  <a name="getversion"></a>CDockState::GetVersion  
 Llame a esta función para recuperar el número de versión de los datos almacenados en la barra de estado.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Valor devuelto  
 1 si la barra almacenada información es anterior a la actual de la barra de estado; 2 si la barra almacenada información es el mismo que el actual estado de la barra.  
  
### <a name="remarks"></a>Comentarios  
 Compatibilidad de versiones permite una barra revisada agregar nuevas propiedades persistentes y seguir siendo capaz de detectar y cargar el estado persistente creado por una versión anterior de la barra.  
  
##  <a name="loadstate"></a>CDockState::LoadState  
 Llame a esta función para recuperar información de estado desde el registro o. Archivo INI.  
  
```  
void LoadState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszProfileName`  
 Apunta a una cadena teminated null que especifica el nombre de una sección en el archivo de inicialización o una clave del registro de Windows donde se almacena información de estado.  
  
### <a name="remarks"></a>Comentarios  
 El nombre del perfil es la sección de la aplicación. INI o el registro que contiene información de estado de las barras. Puede guardar el control de barra de información de estado en el registro o. INI con `SaveState`.  
  
##  <a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo  
 Un `CPtrArray` objeto que es una matriz de punteros a la información de la barra de control almacenado para cada barra de control que ha guardado la información de estado en la `CDockState` objeto.  
  
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
 Apunta a una cadena teminated null que especifica el nombre de una sección en el archivo de inicialización o una clave del registro de Windows donde se almacena información de estado.  
  
### <a name="remarks"></a>Comentarios  
 El nombre del perfil es la sección de la aplicación. Archivo INI o el registro que contiene información de estado de la barra de control. `SaveState`También guarda el tamaño actual de la pantalla. Puede recuperar información de la barra de control del registro o. INI con `LoadState`.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)


