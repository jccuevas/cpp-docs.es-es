---
title: CMFCRibbonQuickAccessToolBarDefaultState (Clase)
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
ms.openlocfilehash: 56219e8ed1833f4b448ec6ffd3c16e9db3c66ada
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368873"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState (Clase)

Una clase auxiliar que administra el estado predeterminado de la barra de herramientas de acceso rápido que se coloca en la barra de la cinta de opciones ( [CMFCRibbonBar (Clase)](../../mfc/reference/cmfcribbonbar-class.md)).

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Construye un objeto `CMFCRibbonQuickAccessToolbarDefaultState`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Agrega un comando al estado predeterminado de la barra de herramientas de acceso rápido. Esto no cambia la barra de herramientas en sí.|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Copia las propiedades de una barra de herramientas de acceso rápido a otra.|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Elimina todos los comandos de la barra de herramientas de acceso rápido. Esto no cambia la barra de herramientas en sí.|

## <a name="remarks"></a>Observaciones

Después de crear la barra de herramientas de acceso rápido en la aplicación, se recomienda establecer su estado predeterminado mediante una llamada a [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Este estado predeterminado se restaura cuando un usuario hace clic en el botón **Restablecer** de la página **Personalizar** del cuadro de diálogo **Opciones** de la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCRibbonQuickAccessToolbarDefaultState` cómo construir un objeto de la clase y cómo agregar un comando al estado predeterminado para la barra de herramientas de acceso rápido.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonquickaccesstoolbar.h

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a>CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

Agrega un comando al estado predeterminado de la barra de herramientas de acceso rápido.

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parámetros

*[in] uiCmd*<br/>
Especifica el identificador de comando.

*[in] bIsVisible*<br/>
Establece la visibilidad del comando cuando la barra de herramientas de acceso rápido está en el estado predeterminado.

### <a name="remarks"></a>Observaciones

Agregar un comando a la CMFCRibbonQuickAccessToolBarDefaultState logra tres resultados. En primer lugar, cada comando agregado aparece en la lista desplegable en el lado derecho de la barra de herramientas de acceso rápido. De esta manera, un usuario puede agregar o quitar fácilmente ese comando de la barra de herramientas de acceso rápido. En segundo lugar, la barra de herramientas de acceso rápido se restablece para mostrar solo los comandos que aparecen como visibles en el estado predeterminado cuando el usuario hace clic en el botón **Restablecer** del cuadro de diálogo **Personalizar.** En tercer lugar, si no ha llamado a [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), la barra de herramientas de acceso rápido utiliza los comandos visibles de esta lista como los comandos visibles predeterminados la primera vez que un usuario ejecuta la aplicación. Después de agregar todos los comandos que desee, llame a [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) para establecer esta instancia como el estado predeterminado de la barra de herramientas de acceso rápido de esa barra de la cinta de opciones.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a>CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

Copia las propiedades de una barra de herramientas de acceso rápido a otra.

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[en] Una referencia al `CMFCRibbonQuickAccessToolBarDefaultState` objeto de origen desde el que se va a copiar.

### <a name="remarks"></a>Observaciones

Este método copia cada `CMFCRibbonQuickAccessToolBarDefaultState` comando del objeto de origen a este objeto mediante el [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) método.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

Construye el objeto de estado predeterminado de la barra de herramientas de acceso rápido.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, la lista de comandos que contiene la nueva instancia de [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) está vacía.

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a>CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

Borra la lista de comandos predeterminados en la barra de herramientas de acceso rápido.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Esta función quita de esta instancia todos los comandos que llama el anterior a [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) agregado.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
