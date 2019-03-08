---
title: CDockState (clase)
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: b8c4b80d7182795d8919adb64491d506325976ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262693"
---
# <a name="cdockstate-class"></a>CDockState (clase)

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
|[CDockState::GetVersion](#getversion)|Recupera el número de versión de almacenado en la barra de estado.|
|[CDockState::LoadState](#loadstate)|Recupera información de estado desde el registro o. Archivo INI.|
|[CDockState::SaveState](#savestate)|Guarda información de estado en el registro o el archivo INI.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Matriz de punteros a almacenado información de estado con una entrada para cada barra de control de acoplamiento.|

## <a name="remarks"></a>Comentarios

El estado de acoplamiento incluye el tamaño y posición de la barra y si se acopla. Al recuperar almacenado acoplar el estado, `CDockState` comprueba la barra de la posición y, si no está visible con la configuración de pantalla actual, la barra de `CDockState` escala de la barra de posición para que sea visible. El propósito principal de `CDockState` es para contener todo el estado de un número de barras de control y para permitir que se puede guardar el estado y cargarse en del registro, la aplicación. Archivo INI, o en formato binario como parte de un `CArchive` contenido del objeto.

La barra de puede ser cualquier control acoplable barras, incluida una barra de herramientas, la barra de estado o la barra de cuadro de diálogo. `CDockState` objetos se escriben y leen a o desde un archivo a través de un `CArchive` objeto.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) recupera la información de estado de toda la ventana de marco `CControlBar` objetos y los coloca en el `CDockState` objeto. A continuación, puede escribir el contenido de la `CDockState` objeto de almacenamiento con [Serialize](../../mfc/reference/cobject-class.md#serialize) o [CDockState::SaveState](#savestate). Si posteriormente desea restaurar el estado de las barras de control en la ventana de marco, puede cargar el estado con `Serialize` o [CDockState::LoadState](#loadstate), a continuación, usar [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) para aplicar el guardado estado de las barras de control de la ventana de marco.

Para obtener más información sobre las barras de control de acoplamiento, consulte los artículos [barras de Control](../../mfc/control-bars.md), [las barras de herramientas: Acoplamiento y flotantes](../../mfc/docking-and-floating-toolbars.md), y [marco Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxadv.h

##  <a name="clear"></a>  CDockState::Clear

Llame a esta función para borrar toda la información de acoplamiento almacenada en el `CDockState` objeto.

```
void Clear();
```

### <a name="remarks"></a>Comentarios

Esto incluye no solo si se acopla la barra o no, pero el tamaño y la posición de la barra y si es visible o no.

##  <a name="getversion"></a>  CDockState::GetVersion

Llame a esta función para recuperar el número de versión de almacenado en la barra de estado.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valor devuelto

1 si la barra almacenada información es anterior a la actual de la barra de estado; 2 si la barra almacenada información es el mismo que el actual estado de la barra.

### <a name="remarks"></a>Comentarios

Compatibilidad de versiones permite que una barra revisada agregar nuevas propiedades persistentes y seguir siendo capaces de detectar y cargar el estado persistente creado por una versión anterior de la barra.

##  <a name="loadstate"></a>  CDockState::LoadState

Llame a esta función para recuperar información de estado del registro o. Archivo INI.

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
Apunta a una cadena null teminated que especifica el nombre de una sección en el archivo de inicialización o una clave del registro de Windows donde se almacena la información de estado.

### <a name="remarks"></a>Comentarios

El nombre del perfil es la sección de la aplicación. Archivo INI o el registro que contiene información de estado de las barras. Puede guardar el control de barra de información de estado en el registro o. El archivo INI con `SaveState`.

##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo

Un `CPtrArray` objeto que es una matriz de punteros a la información de la barra de control almacenado para cada barra de control que ha guardado la información de estado en el `CDockState` objeto.

```
CPtrArray m_arrBarInfo;
```

##  <a name="savestate"></a>  CDockState::SaveState

Llame a esta función para guardar la información de estado en el registro o. Archivo INI.

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
Apunta a una cadena null teminated que especifica el nombre de una sección en el archivo de inicialización o una clave del registro de Windows donde se almacena la información de estado.

### <a name="remarks"></a>Comentarios

El nombre del perfil es la sección de la aplicación. Archivo INI o del registro que contiene información de estado de la barra de control. `SaveState` También guarda el tamaño de pantalla actual. Puede recuperar información de la barra de control del registro o. El archivo INI con `LoadState`.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
