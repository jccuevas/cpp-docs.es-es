---
title: CSnapInPropertyPageImpl (clase)
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
ms.openlocfilehash: dd60afc34b1a2de8f86037eb180aab86a9b8afde
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503080"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl (clase)

Esta clase proporciona métodos para implementar un objeto de la página de propiedades del complemento.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Cambia el estado de la **Aceptar** y **cancelar** botones.|
|[CSnapInPropertyPageImpl::Create](#create)|Inicializa un recién creado `CSnapInPropertyPageImpl` objeto.|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Lo llama el marco cuando el usuario hace clic en el **aplicar ahora** botón mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Lo llama el marco cuando el usuario hace clic en el **ayuda** botón mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Lo llama el marco de trabajo cuando la página actual ya no está activa.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Lo llama el marco cuando el usuario hace clic en el **cancelar** botón y antes de que la cancelación ha tenido lugar.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Lo llama el marco cuando el usuario hace clic en el **restablecer** botón mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Lo llama el marco de trabajo cuando se activa la página actual.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Lo llama el marco cuando el usuario hace clic en el **volver** botón mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Lo llama el marco cuando el usuario hace clic en el **finalizar** botón mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Lo llama el marco cuando el usuario hace clic en el **siguiente** botón mientras usa una hoja de propiedades de tipo asistente.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Reenvía el mensaje actual para todas las páginas de la hoja de propiedades.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Llamada a activar o desactivar el **aplicar ahora** botón.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|El Windows `PROPSHEETPAGE` estructura utilizada por el `CSnapInPropertyPageImpl` objeto.|

## <a name="remarks"></a>Comentarios

`CSnapInPropertyPageImpl` Proporciona una implementación básica de un objeto de la página de propiedades del complemento. Las características básicas de una página de propiedades del complemento se implementan mediante varias interfaces distintas y asignan los tipos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsnap.h

##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose

Llame a esta función después de que se ha realizado un cambio irrecuperable a los datos en una página de una hoja de propiedades modal.

```
void CancelToClose();
```

### <a name="remarks"></a>Comentarios

Esta función se cambiará el **Aceptar** botón a **cerrar** y deshabilitar el **cancelar** botón. Este cambio no se puede cancelar el usuario que un cambio es permanente y las modificaciones de las alertas.

El `CancelToClose` función miembro no hace nada en una hoja de propiedades no modal, porque no tiene una hoja de propiedades no modal un **cancelar** botón de forma predeterminada.

##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Construye un objeto `CSnapInPropertyPageImpl`.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszTitle*<br/>
[in] El título de la página de propiedades.

### <a name="remarks"></a>Comentarios

Para inicializar la estructura subyacente, llame a [CSnapInPropertyPageImpl::Create](#create).

##  <a name="create"></a>  CSnapInPropertyPageImpl::Create

Llame a esta función para inicializar la estructura subyacente de la página de propiedades.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Valor devuelto

Un identificador para un `PROPSHEETPAGE` estructura que contiene los atributos de la hoja de propiedades recién creado.

### <a name="remarks"></a>Comentarios

Primero debe llamar a [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) antes de llamar a esta función.

##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp

`m_psp` es una estructura cuyos miembros almacenan las características de `PROPSHEETPAGE`.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Comentarios

Utilice esta estructura para inicializar la apariencia de una página de propiedades después de se construye.

Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v3) en el SDK de Windows.

##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply

Esta función miembro se llama cuando el usuario hace clic en el **Aceptar** o **aplicar ahora** botón.

```
BOOL OnApply();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se aceptan los cambios; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Antes de `OnApply` se puede llamar el marco de trabajo, debe haber llamado `SetModified` y establezca su parámetro en TRUE. Esto activará el **aplicar ahora** botón tan pronto como el usuario realiza un cambio en la página de propiedades.

Reemplace esta función miembro para especificar qué acción realizada por el programa cuando el usuario hace clic en el **aplicar ahora** botón. Cuando se reemplaza, la función debe devolver TRUE para aceptar los cambios y FALSE para impedir que los cambios surtan efecto.

La implementación predeterminada de `OnApply` devuelve TRUE.

##  <a name="onhelp"></a>  CSnapInPropertyPageImpl::OnHelp

Esta función miembro se llama cuando el usuario hace clic en el **ayuda** botón de la página de propiedades.

```
void OnHelp();
```

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para mostrar la Ayuda de la página de propiedades.

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

Esta función miembro se llama cuando la página ya no es la página activa.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos se actualizan correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para llevar a cabo las tareas de validación de datos especiales.

##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel

Esta función miembro se llama cuando el usuario hace clic en el **cancelar** botón y antes de la cancelación ha tomado una acción.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero para permitir que la operación de cancelación; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para especificar una acción realizada por el programa cuando el usuario hace clic en el **cancelar** botón.

La implementación predeterminada de `OnQueryCancel` devuelve TRUE.

##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset

Esta función miembro se llama cuando el usuario hace clic en el **cancelar** botón.

```
void OnReset();
```

### <a name="remarks"></a>Comentarios

Cuando se llama a esta función, los cambios en todas las páginas de propiedades que se han realizado por el usuario anteriormente al hacer clic en el **aplicar ahora** botón se descartan y la hoja de propiedades conserva el foco.

Reemplace esta función miembro para especificar qué acción realizada por el programa cuando el usuario hace clic en el **cancelar** botón.

##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive

Esta función miembro se llama cuando la página se ha elegido por el usuario y se convierte en la página activa.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la página se estableció correctamente active; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para llevar a cabo las tareas cuando se activa una página. La invalidación de esta función miembro debe llamar a la versión predeterminada antes de realiza cualquier otro procesamiento.

La implementación predeterminada devuelve TRUE.

##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack

Esta función miembro se llama cuando el usuario hace clic en el **volver** botón en un asistente.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Valor devuelto

- 0 para pasar automáticamente a la página anterior.

- -1 para impedir que cambien la página.

Para saltar a una página distinta de la siguiente, devolver el identificador del cuadro de diálogo que se mostrará.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para especificar alguna acción que debe realizar cuando el usuario la **volver** se hace clic en el botón.

##  <a name="onwizardfinish"></a>  CSnapInPropertyPageImpl::OnWizardFinish

Esta función miembro se llama cuando el usuario hace clic en el **finalizar** botón en un asistente.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se destruye cuando finalice el Asistente; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para especificar alguna acción que debe realizar cuando el usuario la **finalizar** se hace clic en el botón.

##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext

Esta función miembro se llama cuando el usuario hace clic en el **siguiente** botón en un asistente.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Valor devuelto

- 0 para pasar automáticamente a la página siguiente.

- -1 para impedir que cambien la página.

Para saltar a una página distinta de la siguiente, devolver el identificador del cuadro de diálogo que se mostrará.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para especificar alguna acción que debe realizar cuando el usuario la **siguiente** se hace clic en el botón.

##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings

Llame a esta función miembro para reenviar un mensaje a cada página en la hoja de propiedades.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*wParam*<br/>
[in] Especifica información adicional de dependiente del mensaje.

*lParam*<br/>
[in] Especifica información adicional de dependiente del mensaje.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no se debe reenviar el mensaje a la siguiente página de propiedades; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si una página, devuelve un valor distinto de cero, la hoja de propiedades no envía el mensaje a las páginas siguientes.

##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified

Llame a esta función miembro para habilitar o deshabilitar la **aplicar ahora** botón, en función de si se debe aplicar la configuración en la página de propiedades en el objeto externo adecuado.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parámetros

*bChanged*<br/>
[in] TRUE para indicar que la configuración de la página de propiedades se han modificado desde la última vez que se aplicaron; FALSE para indicar que la configuración de la página de propiedades se han aplicado o que debe omitirse.

### <a name="remarks"></a>Comentarios

La hoja de propiedades realiza el seguimiento de las páginas son "sucios", es decir, páginas de propiedades para el que ha llamado `SetModified( TRUE )`. El **aplicar ahora** botón siempre estará habilitado si se llama a `SetModified( TRUE )` para una de las páginas. El **aplicar ahora** botón se deshabilitará cuando se llama a `SetModified( FALSE )` para una de las páginas, pero sólo si ninguna de las otras páginas está "sucio".

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
