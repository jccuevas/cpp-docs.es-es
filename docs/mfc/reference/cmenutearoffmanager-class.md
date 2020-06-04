---
title: Clase CMenuTearOffManager
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: 6aef644cb7364184df91a6e8caee18cac65af4cc
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751808"
---
# <a name="cmenutearoffmanager-class"></a>Clase CMenuTearOffManager

Administra menús con barra desplazable. Un menú con barra desplazable es un menú de la barra de menús. El usuario puede quitar un menú con barra desplazable de la barra de menús y provocar que el menú con barra desplazable quede flotante.

   Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|Construye un objeto `CMenuTearOffManager`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMenuTearOffManager::Build](#build)||
|[CMenuTearOffManager::GetRegPath](#getregpath)||
|[CMenuTearOffManager::Initialize](#initialize)|Inicializa un objeto `CMenuTearOffManager`.|
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||
|[CMenuTearOffManager::Parse](#parse)||
|[CMenuTearOffManager::Reset](#reset)||
|[CMenuTearOffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>Observaciones

Para utilizar menús de desmontaje en la `CMenuTearOffManager` aplicación, debe tener un objeto. En la mayoría de los casos, `CMenuTearOffManager` no creará ni inicializará un objeto directamente. Esto se controla para usted cuando se llama a la [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) función.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMenuTearOffManager` cómo construir `CWinAppEX::EnableTearOffMenus` e inicializar un objeto mediante una llamada al método. Este fragmento de código forma parte del [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmenutearoffmanager.h

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a>CMenuTearOffManager::Build

```cpp
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>Parámetros

[en] *uiTearOffBarID*<br/>

[en] *strText*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a>CMenuTearOffManager::CMenuTearOffManager

Construye un [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objeto.

```
CMenuTearOffManager();
```

### <a name="remarks"></a>Observaciones

En la mayoría de los `CMenuTearOffManager` casos, no debe crear un manualmente. El marco de trabajo `CMenuTearOffManager` de la aplicación crea el objeto cuando se llama a [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a>CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a>CMenuTearOffManager::Initialize

Inicializa un [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objeto.

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>Parámetros

*lpszRegEntry*<br/>
[en] Cadena que contiene la ruta de acceso de una entrada del Registro. Las aplicaciones almacenan la configuración de las barras de desmontaje en esta entrada del Registro.

*uiTearOffMenuFirst*<br/>
[en] El primer ID de menú para un menú de desmontaje.

*uiTearOffMenuLast*<br/>
[en] El último ID de menú para un menú de desmontaje.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El intervalo de los iDE de menú de *uiTearOffMenuFirst* a *uiTearOffMenuLast* debe ser un intervalo continuo. El intervalo define el número de menús de desmontaje que pueden aparecer al mismo tiempo en la aplicación.

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>Parámetros

[en] *uiID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a>CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>Parámetros

[en] *str*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a>CMenuTearOffManager::Reset

```cpp
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>Parámetros

[en] *hmenu*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a>CMenuTearOffManager::SetInUse

```cpp
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>Parámetros

[en] *uiCmdId*<br/>

[en] *bUse*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus

```cpp
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

[en] *hMenú*<br/>

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)
