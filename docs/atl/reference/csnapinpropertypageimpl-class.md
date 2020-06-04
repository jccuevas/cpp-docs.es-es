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
ms.openlocfilehash: 3f09e8500eadd36eec53db95f10261834d672101
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747581"
---
# <a name="csnapinpropertypageimpl-class"></a>Clase CSnapInPropertyPageImpl

Esta clase proporciona métodos para implementar un objeto de página de propiedades de complemento.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Cambia el estado de los botones **Aceptar** y **Cancelar.**|
|[CSnapInPropertyPageImpl::Crear](#create)|Inicializa un objeto `CSnapInPropertyPageImpl` recién creado.|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Llamado por el marco de trabajo cuando el usuario hace clic en el **botón Aplicar ahora** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Llamado por el marco de trabajo cuando el usuario hace clic en el botón **Ayuda** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Llamado por el marco de trabajo cuando la página actual ya no está activa.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Llamado por el marco de trabajo cuando el usuario hace clic en el **botón Cancelar** y antes de que se haya realizado la cancelación.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Llamado por el marco de trabajo cuando el usuario hace clic en el botón **Restablecer** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Llamado por el marco de trabajo cuando la página actual se activa.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Llamado por el marco de trabajo cuando el usuario hace clic en el **botón Atrás** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Llamado por el marco de trabajo cuando el usuario hace clic en el botón **Finalizar** mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Llamado por el marco de trabajo cuando el usuario hace clic en el **siguiente** botón mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Reenvía el mensaje actual a todas las páginas de la hoja de propiedades.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Llame para activar o desactivar el botón **Aplicar ahora.**|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|La `PROPSHEETPAGE` estructura de `CSnapInPropertyPageImpl` Windows utilizada por el objeto.|

## <a name="remarks"></a>Observaciones

`CSnapInPropertyPageImpl`proporciona una implementación básica para un objeto de página de propiedades de complemento. Las características básicas de una página de propiedades de complemento se implementan mediante varias interfaces y tipos de mapa diferentes.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsnap.h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose

Llame a esta función después de que se haya realizado un cambio irrecuperable en los datos de una página de una hoja de propiedades modal.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Observaciones

Esta función cambiará el botón **Aceptar** a **Cerrar** y desactivará el botón **Cancelar.** Este cambio alerta al usuario de que un cambio es permanente y que las modificaciones no se pueden cancelar.

La `CancelToClose` función miembro no hace nada en una hoja de propiedades no esquemética, porque una hoja de propiedades no es mide no tiene un botón **Cancelar** de forma predeterminada.

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Construye un objeto `CSnapInPropertyPageImpl`.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszTitle*<br/>
[en] El título de la página de propiedades.

### <a name="remarks"></a>Observaciones

Para inicializar la estructura subyacente, llame a [CSnapInPropertyPageImpl::Create](#create).

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapInPropertyPageImpl::Crear

Llame a esta función para inicializar la estructura subyacente de la página de propiedades.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Valor devuelto

Identificador de `PROPSHEETPAGE` una estructura que contiene los atributos de la hoja de propiedades recién creada.

### <a name="remarks"></a>Observaciones

Primero debe llamar a [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) antes de llamar a esta función.

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp

`m_psp`es una estructura cuyos `PROPSHEETPAGE`miembros almacenan las características de .

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Observaciones

Utilice esta estructura para inicializar la apariencia de una página de propiedades después de construirla.

Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) en el Windows SDK.

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapInPropertyPageImpl::OnApply

Esta función miembro se llama cuando el usuario hace clic en el **Aceptar** o el **aplicar ahora** botón.

```
BOOL OnApply();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se aceptan los cambios; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Antes `OnApply` de que el marco de `SetModified` trabajo pueda llamar a ella, debe haber llamado y establecido su parámetro en TRUE. Esto activará el botón **Aplicar ahora** tan pronto como el usuario realice un cambio en la página de propiedades.

Invalide esta función miembro para especificar qué acción realiza el programa cuando el usuario hace clic en el botón **Aplicar ahora.** Al reemplazar, la función debe devolver TRUE para aceptar cambios y FALSE para evitar que los cambios surtan efecto.

La implementación `OnApply` predeterminada de devuelve TRUE.

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp

Esta función miembro se llama cuando el usuario hace clic en el botón **Ayuda** para la página de propiedades.

```cpp
void OnHelp();
```

### <a name="remarks"></a>Observaciones

Invalidar esta función miembro para mostrar ayuda para la página de propiedades.

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive

Se llama a esta función miembro cuando la página ya no es la página activa.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos se actualizaron correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para realizar tareas especiales de validación de datos.

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel

Esta función miembro se llama cuando el usuario hace clic en el **cancelar** botón y antes de que se ha realizado la acción de cancelación.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero para permitir la operación de cancelación; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para especificar una acción que el programa realiza cuando el usuario hace clic en el **botón Cancelar.**

La implementación `OnQueryCancel` predeterminada de devuelve TRUE.

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a>CSnapInPropertyPageImpl::OnReset

Esta función miembro se llama cuando el usuario hace clic en el **cancelar** botón.

```cpp
void OnReset();
```

### <a name="remarks"></a>Observaciones

Cuando se llama a esta función, se descartan los cambios realizados en todas las páginas de propiedades realizadas por el usuario haciendo clic anteriormente en el botón **Aplicar ahora** y la hoja de propiedades conserva el foco.

Invalide esta función miembro para especificar qué acción realiza el programa cuando el usuario hace clic en el **botón Cancelar.**

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive

Esta función miembro se llama cuando el usuario elige la página y se convierte en la página activa.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la página se estableció correctamente activa; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para realizar tareas cuando se activa una página. La invalidación de esta función miembro debe llamar a la versión predeterminada antes de que se realice cualquier otro procesamiento.

La implementación predeterminada devuelve TRUE.

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack

Esta función miembro se llama cuando el usuario hace clic en el **botón Atrás** en un asistente.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Valor devuelto

- 0 para avanzar automáticamente a la página anterior.

- -1 para evitar que la página cambie.

Para saltar a una página que no sea la siguiente, devuelva el identificador del cuadro de diálogo que se va a mostrar.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se hace clic en el botón **Atrás.**

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish

Esta función miembro se llama cuando el usuario hace clic en el **finalizar** botón en un asistente.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se destruye cuando finaliza el asistente; de lo contrario cero.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se hace clic en el botón **Finalizar.**

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext

Esta función miembro se llama cuando el usuario hace clic en el **siguiente** botón en un asistente.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Valor devuelto

- 0 para avanzar automáticamente a la página siguiente.

- -1 para evitar que la página cambie.

Para saltar a una página que no sea la siguiente, devuelva el identificador del cuadro de diálogo que se va a mostrar.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se hace clic en el botón **Siguiente.**

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings

Llame a esta función miembro para reenviar un mensaje a cada página de la hoja de propiedades.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*wParam*<br/>
[en] Especifica información adicional dependiente del mensaje.

*lParam*<br/>
[en] Especifica información adicional dependiente del mensaje.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mensaje no se debe reenviar a la siguiente página de propiedades; de lo contrario cero.

### <a name="remarks"></a>Observaciones

Si una página devuelve un valor distinto de cero, la hoja de propiedades no envía el mensaje a las páginas posteriores.

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified

Llame a esta función miembro para habilitar o deshabilitar el **botón Aplicar ahora,** en función de si la configuración de la página de propiedades se debe aplicar al objeto externo adecuado.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parámetros

*bChanged*<br/>
[en] TRUE para indicar que la configuración de la página de propiedades se ha modificado desde la última vez que se aplicaron; FALSE para indicar que se ha aplicado la configuración de la página de propiedades o se debe omitir.

### <a name="remarks"></a>Observaciones

La hoja de propiedades realiza un seguimiento de qué páginas están `SetModified( TRUE )`"sucias", es decir, las páginas de propiedades para las que ha llamado . El botón **Aplicar ahora** siempre estará `SetModified( TRUE )` habilitado si llama a una de las páginas. El botón **Aplicar ahora** se `SetModified( FALSE )` deshabilitará cuando llame a una de las páginas, pero solo si ninguna de las otras páginas está "sucia".

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
