---
title: CMFCRibbonQuickAccessToolBarDefaultState (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: 0ea9ec8de0b657fa4e7c601f9c3e676f550defa9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302486"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState (clase)

Una clase auxiliar que administra el estado predeterminado para la barra de herramientas de acceso rápido que está situado en la barra de cinta ( [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)).

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Construye un objeto `CMFCRibbonQuickAccessToolbarDefaultState`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Agrega un comando al estado predeterminado para la barra de herramientas de acceso rápido. Esto no cambia la barra de herramientas.|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Copia las propiedades de una barra de herramientas de acceso rápido a otra.|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Quita todos los comandos de la barra de herramientas de acceso rápido. Esto no cambia la barra de herramientas.|

## <a name="remarks"></a>Comentarios

Después de crear la barra de herramientas de acceso rápido en la aplicación, se recomienda establecer su estado predeterminado mediante una llamada a [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Este estado predeterminado se restaura cuando un usuario hace clic en el **restablecer** situado en la **personalizar** página de la aplicación **opciones** cuadro de diálogo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonQuickAccessToolbarDefaultState` clase y cómo agregar un comando al estado predeterminado para la barra de herramientas de acceso rápido.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonquickaccesstoolbar.h

##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

Agrega un comando al estado predeterminado para la barra de herramientas de acceso rápido.

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parámetros

*[in] uiCmd*<br/>
Especifica el identificador de comando.

*[in] bIsVisible*<br/>
Establece la visibilidad del comando cuando la barra de herramientas de acceso rápido se encuentra en el estado predeterminado.

### <a name="remarks"></a>Comentarios

Agregar un comando a la CMFCRibbonQuickAccessToolBarDefaultState lleva a cabo tres resultados. En primer lugar, cada comando agregado aparece en la lista desplegable en el lado derecho de la barra de herramientas de acceso rápido. De esta manera, un usuario puede agregar o quitar el comando de la barra de herramientas de acceso rápido fácilmente. En segundo lugar, se restablece la barra de herramientas de acceso rápido para mostrar únicamente los comandos que aparecen como visible en el estado predeterminado cuando el usuario hace clic en el **restablecer** situado en la **personalizar** cuadro de diálogo. Tercero, si no ha llamado a [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), la barra de herramientas de acceso rápido usa los comandos de esta lista visibles como comandos visibles de forma predeterminada la primera vez que un usuario ejecuta la aplicación. Después de haber agregado todos los comandos que desee, llame a [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) para establecer esta instancia como el estado predeterminado para la barra de herramientas de acceso rápido de esa barra de cinta.

##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

Copia las propiedades de una barra de herramientas de acceso rápido a otra.

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[in] Una referencia al origen de `CMFCRibbonQuickAccessToolBarDefaultState` objeto que se va a copiar desde.

### <a name="remarks"></a>Comentarios

Este método copia cada comando desde el origen `CMFCRibbonQuickAccessToolBarDefaultState` objeto a este objeto utilizando el [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) método.

##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

Construye el objeto de estado de la barra de herramientas de acceso rápido de forma predeterminada.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, la lista de comandos que la nueva instancia de [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) contiene está vacío.

##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

Borra la lista de comandos de forma predeterminada en la barra de herramientas de acceso rápido.

```
void RemoveAll();
```

### <a name="remarks"></a>Comentarios

Esta función quita de esta instancia de todos los comandos que las llamadas anteriores a [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) agregado.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
