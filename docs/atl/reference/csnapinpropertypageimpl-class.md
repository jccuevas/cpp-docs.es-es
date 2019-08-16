---
title: Clase CSnapInPropertyPageImpl
ms.date: 11/04/2016
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: abf4cf5804f6ef7335192feb298f1a4a06f841e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496391"
---
# <a name="csnapinpropertypageimpl-class"></a>Clase CSnapInPropertyPageImpl

Esta clase proporciona métodos para implementar un objeto de página de propiedades de complemento.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Cambia el estado de los botones **Aceptar** y **Cancelar** .|
|[CSnapInPropertyPageImpl::Create](#create)|Inicializa un objeto recién creado `CSnapInPropertyPageImpl` .|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Lo llama el marco de trabajo cuando el usuario hace clic en el botón **aplicar ahora** mientras usa una hoja de propiedades de tipo de asistente.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Lo llama el marco de trabajo cuando el usuario hace clic en el botón **ayuda** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Lo llama el marco de trabajo cuando la página actual ya no está activa.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Lo llama el marco de trabajo cuando el usuario hace clic en el botón **Cancelar** y antes de que haya tenido lugar la cancelación.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Lo llama el marco de trabajo cuando el usuario hace clic en el botón **restablecer** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Lo llama el marco de trabajo cuando se activa la página actual.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Lo llama el marco de trabajo cuando el usuario hace clic en el botón **atrás** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Lo llama el marco de trabajo cuando el usuario hace clic en el botón **Finalizar** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Lo llama el marco de trabajo cuando el usuario hace clic en el botón **siguiente** mientras usa una hoja de propiedades de tipo de asistente.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Reenvía el mensaje actual a todas las páginas de la hoja de propiedades.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Llame a para activar o desactivar el botón **aplicar ahora** .|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Estructura de `PROPSHEETPAGE` Windows utilizada por el `CSnapInPropertyPageImpl` objeto.|

## <a name="remarks"></a>Comentarios

`CSnapInPropertyPageImpl`proporciona una implementación básica para un objeto de página de propiedades de complemento. Las características básicas de una página de propiedades de complemento se implementan utilizando varias interfaces y tipos de mapa diferentes.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsnap. h

##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose

Llame a esta función después de que se haya realizado un cambio irrecuperable en los datos de una página de una hoja de propiedades modal.

```
void CancelToClose();
```

### <a name="remarks"></a>Comentarios

Esta función cambiará el botón **Aceptar** para **cerrar** y deshabilitar el botón **Cancelar** . Este cambio avisa al usuario de que un cambio es permanente y las modificaciones no se pueden cancelar.

La `CancelToClose` función miembro no hace nada en una hoja de propiedades no modal, porque una hoja de propiedades no modal no tiene un botón **Cancelar** de forma predeterminada.

##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Construye un objeto `CSnapInPropertyPageImpl`.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszTitle*<br/>
de Título de la página de propiedades.

### <a name="remarks"></a>Comentarios

Para inicializar la estructura subyacente, llame a [CSnapInPropertyPageImpl:: Create](#create).

##  <a name="create"></a>  CSnapInPropertyPageImpl::Create

Llame a esta función para inicializar la estructura subyacente de la página de propiedades.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Valor devuelto

Identificador de una `PROPSHEETPAGE` estructura que contiene los atributos de la hoja de propiedades recién creada.

### <a name="remarks"></a>Comentarios

Primero debe llamar a [CSnapInPropertyPageImpl:: CSnapInPropertyPageImpl](#csnapinpropertypageimpl) antes de llamar a esta función.

##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp

`m_psp`es una estructura cuyos miembros almacenan las características `PROPSHEETPAGE`de.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Comentarios

Use esta estructura para inicializar la apariencia de una página de propiedades después de construirla.

Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) en el Windows SDK.

##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply

Se llama a esta función miembro cuando el usuario hace clic en el botón **Aceptar** o **aplicar ahora** .

```
BOOL OnApply();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se aceptan los cambios; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Antes `OnApply` de que el marco de trabajo pueda llamarlo, debe `SetModified` haber llamado a y establecer su parámetro en true. Se activará el botón **aplicar ahora** en cuanto el usuario realice un cambio en la página de propiedades.

Invalide esta función miembro para especificar la acción que realizará el programa cuando el usuario haga clic en el botón **aplicar ahora** . Al reemplazar, la función debe devolver TRUE para aceptar los cambios y FALSE para evitar que los cambios surtan efecto.

La implementación predeterminada de `OnApply` devuelve true.

##  <a name="onhelp"></a>  CSnapInPropertyPageImpl::OnHelp

Se llama a esta función miembro cuando el usuario hace clic en el botón **ayuda** de la página de propiedades.

```
void OnHelp();
```

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para mostrar la ayuda de la página de propiedades.

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

Se llama a esta función miembro cuando la página ya no es la página activa.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos se actualizaron correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para realizar tareas de validación de datos especiales.

##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel

Se llama a esta función miembro cuando el usuario hace clic en el botón **Cancelar** y antes de que se realice la acción de cancelación.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero para permitir la operación de cancelación; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para especificar una acción que el programa realiza cuando el usuario hace clic en el botón **Cancelar** .

La implementación predeterminada de `OnQueryCancel` devuelve true.

##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset

Se llama a esta función miembro cuando el usuario hace clic en el botón **Cancelar** .

```
void OnReset();
```

### <a name="remarks"></a>Comentarios

Cuando se llama a esta función, se descartan los cambios en todas las páginas de propiedades realizadas por el usuario anteriormente al hacer clic en el botón **aplicar ahora** y la hoja de propiedades conserva el foco.

Invalide esta función miembro para especificar qué acción realiza el programa cuando el usuario hace clic en el botón **Cancelar** .

##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive

Se llama a esta función miembro cuando el usuario elige la página y se convierte en la página activa.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la página se estableció correctamente activa; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para realizar tareas cuando se activa una página. La invalidación de esta función miembro debe llamar a la versión predeterminada antes de que se realice cualquier otro procesamiento.

La implementación predeterminada devuelve TRUE.

##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack

Se llama a esta función miembro cuando el usuario hace clic en el botón **atrás** en un asistente.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Valor devuelto

- 0 para avanzar automáticamente a la página anterior.

- -1 para evitar que la página cambie.

Para saltar a una página que no sea la siguiente, devuelva el identificador del cuadro de diálogo que se va a mostrar.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se haga clic en el botón **atrás** .

##  <a name="onwizardfinish"></a>  CSnapInPropertyPageImpl::OnWizardFinish

Se llama a esta función miembro cuando el usuario hace clic en el botón **Finalizar** en un asistente.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se destruye cuando finaliza el asistente; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se haga clic en el botón **Finalizar** .

##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext

Se llama a esta función miembro cuando el usuario hace clic en el botón **siguiente** en un asistente.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Valor devuelto

- 0 para avanzar automáticamente a la página siguiente.

- -1 para evitar que la página cambie.

Para saltar a una página que no sea la siguiente, devuelva el identificador del cuadro de diálogo que se va a mostrar.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se haga clic en el botón **siguiente** .

##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings

Llame a esta función miembro para reenviar un mensaje a cada página de la hoja de propiedades.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*wParam*<br/>
de Especifica información adicional dependiente del mensaje.

*lParam*<br/>
de Especifica información adicional dependiente del mensaje.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el mensaje no se debe reenviar a la página de propiedades siguiente; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

Si una página devuelve un valor distinto de cero, la hoja de propiedades no envía el mensaje a las páginas siguientes.

##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified

Llame a esta función miembro para habilitar o deshabilitar el botón **aplicar ahora** , en función de si la configuración de la página de propiedades se debe aplicar al objeto externo adecuado.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parámetros

*bChanged*<br/>
de TRUE para indicar que la configuración de la página de propiedades se ha modificado desde la última vez que se aplicaron; FALSE para indicar que se ha aplicado la configuración de la página de propiedades o se debe omitir.

### <a name="remarks"></a>Comentarios

La hoja de propiedades realiza un seguimiento de las páginas que están "desfasadas", es decir, las páginas de propiedades `SetModified( TRUE )`para las que se ha llamado. El botón **aplicar ahora** siempre estará habilitado si se llama `SetModified( TRUE )` a para una de las páginas. El botón **aplicar ahora** se deshabilitará cuando se `SetModified( FALSE )` llame a para una de las páginas, pero solo si ninguna de las otras páginas está "desfasada".

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
