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
ms.openlocfilehash: 9850486407ee7550ee866a10e656d45ad18fc196
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753263"
---
# <a name="cdockstate-class"></a>CDockState (clase)

Una clase serializada `CObject` que carga, descarga o desactiva el estado de una o más barras de control de acoplamiento en memoria persistente (un archivo).

## <a name="syntax"></a>Sintaxis

```
class CDockState : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDockState::Clear](#clear)|Borra la información de estado del dock.|
|[CDockState::GetVersion](#getversion)|Recupera el número de versión del estado de la barra almacenada.|
|[CDockState::LoadState](#loadstate)|Recupera información de estado del registro o . Archivo INI.|
|[CDockState::SaveState](#savestate)|Guarda la información de estado en el registro o en el archivo INI.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Matriz de punteros a la información de estado de acoplamiento almacenada con una entrada para cada barra de control.|

## <a name="remarks"></a>Observaciones

El estado del muelle incluye el tamaño y la posición de la barra y si está o no acoplada. Al recuperar el estado `CDockState` de acoplamiento almacenado, comprueba la posición de la barra y, `CDockState` si la barra no está visible con la configuración de pantalla actual, escala la posición de la barra para que sea visible. El propósito `CDockState` principal de es mantener todo el estado de un número de barras de control y permitir que ese estado se guarde y cargue ya sea en el registro, el de la aplicación. INI, o en forma binaria `CArchive` como parte del contenido de un objeto.

La barra puede ser cualquier barra de control acoplable, incluida una barra de herramientas, una barra de estado o una barra de diálogo. `CDockState`objetos se escriben y se `CArchive` leen a o desde un archivo a través de un objeto.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) recupera la información de estado de `CControlBar` todos los objetos `CDockState` de la ventana de marco y la coloca en el objeto. A continuación, puede escribir `CDockState` el contenido del objeto en el almacenamiento con [Serialize](../../mfc/reference/cobject-class.md#serialize) o [CDockState::SaveState](#savestate). Si más adelante desea restaurar el estado de las barras de control `Serialize` en la ventana de marco, puede cargar el estado con o [CDockState::LoadState](#loadstate), a continuación, utilice [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) para aplicar el estado guardado a las barras de control de la ventana de marco.

Para obtener más información sobre las barras de control de acoplamiento, consulte los artículos [Barras](../../mfc/control-bars.md)de control , [Barras de herramientas: Acoplamiento y flotante](../../mfc/docking-and-floating-toolbars.md)y [Ventanas](../../mfc/frame-windows.md)de marco .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxadv.h

## <a name="cdockstateclear"></a><a name="clear"></a>CDockState::Clear

Llame a esta función para borrar `CDockState` toda la información de acoplamiento almacenada en el objeto.

```cpp
void Clear();
```

### <a name="remarks"></a>Observaciones

Esto incluye no sólo si la barra está acoplada o no, sino el tamaño y la posición de la barra y si es visible o no.

## <a name="cdockstategetversion"></a><a name="getversion"></a>CDockState::GetVersion

Llame a esta función para recuperar el número de versión del estado de la barra almacenada.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valor devuelto

1 si la información de la barra almacenada es anterior al estado actual de la barra; 2 si la información de la barra almacenada es la misma que el estado actual de la barra.

### <a name="remarks"></a>Observaciones

La compatibilidad con versiones permite que una barra revisada agregue nuevas propiedades persistentes y aún pueda detectar y cargar el estado persistente creado por una versión anterior de la barra.

## <a name="cdockstateloadstate"></a><a name="loadstate"></a>CDockState::LoadState

Llame a esta función para recuperar información de estado del registro o . Archivo INI.

```cpp
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
Apunta a una cadena de valores NULL que especifica el nombre de una sección en el archivo de inicialización o una clave en el registro de Windows donde se almacena la información de estado.

### <a name="remarks"></a>Observaciones

El nombre del perfil es la sección de la aplicación. INI o el registro que contiene la información de estado de las barras. Puede guardar la información de estado de la barra de control en el registro o . INI con `SaveState`.

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo

Objeto `CPtrArray` que es una matriz de punteros a la información de la barra `CDockState` de control almacenada para cada barra de control que ha guardado información de estado en el objeto.

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a>CDockState::SaveState

Llame a esta función para guardar la información de estado en el registro o . Archivo INI.

```cpp
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
Apunta a una cadena de valores NULL que especifica el nombre de una sección en el archivo de inicialización o una clave en el registro de Windows donde se almacena la información de estado.

### <a name="remarks"></a>Observaciones

El nombre del perfil es la sección de la aplicación. INI o el registro que contiene la información de estado de la barra de control. `SaveState`también guarda el tamaño de pantalla actual. Puede recuperar información de la barra de control del registro o . INI con `LoadState`.

## <a name="see-also"></a>Vea también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
