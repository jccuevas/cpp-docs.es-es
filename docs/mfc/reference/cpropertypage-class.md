---
title: CPropertyPage (clase)
ms.date: 11/04/2016
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
ms.openlocfilehash: f9116306fd2bd6145096b055025bd4dd2075b0c1
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916875"
---
# <a name="cpropertypage-class"></a>CPropertyPage (clase)

Representa páginas individuales de una hoja de propiedades, también conocidas como cuadro de diálogo de pestaña.

## <a name="syntax"></a>Sintaxis

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|Construye un objeto `CPropertyPage`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPropertyPage::CancelToClose](#canceltoclose)|Cambia el botón Aceptar para leer Close y deshabilita el botón Cancelar, después de un cambio irrecuperable en la página de una hoja de propiedades modal.|
|[CPropertyPage::Construct](#construct)|Construye un objeto `CPropertyPage`. Utilice `Construct` si desea especificar los parámetros en tiempo de ejecución o si está utilizando matrices.|
|[CPropertyPage::GetPSP](#getpsp)|Recupera la estructura [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) de Windows asociada `CPropertyPage` al objeto.|
|[CPropertyPage::OnApply](#onapply)|Lo llama el marco de trabajo cuando se hace clic en el botón aplicar ahora.|
|[CPropertyPage::OnCancel](#oncancel)|Lo llama el marco de trabajo cuando se hace clic en el botón Cancelar.|
|[CPropertyPage::OnKillActive](#onkillactive)|Lo llama el marco de trabajo cuando la página actual ya no es la página activa. Realice la validación de datos aquí.|
|[CPropertyPage::OnOK](#onok)|Lo llama el marco de trabajo cuando se hace clic en el botón Aceptar, aplicar ahora o cerrar.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Lo llama el marco de trabajo cuando se hace clic en el botón Cancelar y antes de que se realice la cancelación.|
|[CPropertyPage::OnReset](#onreset)|Lo llama el marco de trabajo cuando se hace clic en el botón Cancelar.|
|[CPropertyPage::OnSetActive](#onsetactive)|Lo llama el marco de trabajo cuando la página se convierte en la página activa.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Lo llama el marco de trabajo cuando se hace clic en el botón atrás mientras se usa una hoja de propiedades de tipo asistente.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Lo llama el marco de trabajo cuando se hace clic en el botón Finalizar mientras se usa una hoja de propiedades de tipo asistente.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Lo llama el marco de trabajo cuando se hace clic en el botón siguiente mientras se usa una hoja de propiedades de tipo asistente.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Reenvía el mensaje a cada página de la hoja de propiedades.|
|[CPropertyPage::SetModified](#setmodified)|Llame a para activar o desactivar el botón aplicar ahora.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Estructura [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) de Windows. Proporciona acceso a los parámetros de la página de propiedades básica.|

## <a name="remarks"></a>Comentarios

Al igual que con los cuadros de diálogo estándar, se `CPropertyPage` deriva una clase de para cada página de la hoja de propiedades. Para usar `CPropertyPage`objetos derivados de, cree primero un objeto [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) y, a continuación, cree un objeto para cada página que se dirige a la hoja de propiedades. Llame a [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) para cada página de la hoja y, a continuación, muestre la hoja de propiedades mediante una llamada a [CPropertySheet::D omodal](../../mfc/reference/cpropertysheet-class.md#domodal) para una hoja de propiedades modal, o a [CPropertySheet:: Create](../../mfc/reference/cpropertysheet-class.md#create) para una hoja de propiedades no modal.

Puede crear un tipo de cuadro de diálogo de pestaña denominado asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades que guía al usuario a través de los pasos de una operación, como la configuración de un dispositivo o la creación de un boletín. En un cuadro de diálogo de ficha tipo de asistente, las páginas de propiedades no tienen pestañas y solo se puede ver una página de propiedades a la vez. Además, en lugar de tener botones aceptar y aplicar ahora, un cuadro de diálogo de la pestaña tipo asistente tiene un botón atrás, un botón siguiente o finalizar y un botón Cancelar.

Para obtener más información sobre cómo establecer una hoja de propiedades como un asistente, vea [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Para obtener más información sobre `CPropertyPage` el uso de objetos, vea el artículo [hojas de propiedades y páginas de propiedades](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs. h

##  <a name="canceltoclose"></a>  CPropertyPage::CancelToClose

Llame a esta función después de que se haya realizado un cambio irrecuperable en los datos de una página de una hoja de propiedades modal.

```
void CancelToClose();
```

### <a name="remarks"></a>Comentarios

Esta función cambiará el botón Aceptar para cerrar y deshabilitar el botón Cancelar. Este cambio avisa al usuario de que un cambio es permanente y las modificaciones no se pueden cancelar.

La `CancelToClose` función miembro no hace nada en una hoja de propiedades no modal, porque una hoja de propiedades no modal no tiene un botón Cancelar de forma predeterminada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage:: QuerySiblings](#querysiblings).

##  <a name="construct"></a>  CPropertyPage::Construct

Llame a esta función miembro para construir `CPropertyPage` un objeto.

```
void Construct(
    UINT nIDTemplate,
    UINT nIDCaption = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0);

void Construct(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);
```

### <a name="parameters"></a>Parámetros

*nIDTemplate*<br/>
IDENTIFICADOR de la plantilla utilizada para esta página.

*nIDCaption*<br/>
IDENTIFICADOR del nombre que se va a colocar en la pestaña de esta página. Si es 0, el nombre se tomará de la plantilla de cuadro de diálogo de esta página.

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla.

*nIDHeaderTitle*<br/>
IDENTIFICADOR del nombre que se va a colocar en la ubicación del título del encabezado de la página de propiedades. De forma predeterminada, es 0.

*nIDHeaderSubTitle*<br/>
IDENTIFICADOR del nombre que se va a colocar en la ubicación del subtítulo del encabezado de la página de propiedades. De forma predeterminada, es 0.

### <a name="remarks"></a>Comentarios

El objeto se muestra cuando se cumplen todas las condiciones siguientes:

- La página se ha agregado a una hoja de propiedades mediante [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Se ha llamado a la función [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) o [Create](../../mfc/reference/cpropertysheet-class.md#create) de la hoja de propiedades.

- El usuario ha seleccionado (con pestañas) esta página.

Llame `Construct` a si no se ha llamado a uno de los otros constructores de clase. La `Construct` función miembro es flexible porque puede dejar la instrucción Parameter en blanco y, a continuación, especificar varios parámetros y construcción en cualquier punto del código.

Debe usar `Construct` al trabajar con matrices y debe llamar `Construct` a para cada miembro de la matriz, de modo que se asignen los valores adecuados a los miembros de datos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>  CPropertyPage::CPropertyPage

Construye un objeto `CPropertyPage`.

```
CPropertyPage();

explicit CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

explicit CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```

### <a name="parameters"></a>Parámetros

*nIDTemplate*<br/>
IDENTIFICADOR de la plantilla utilizada para esta página.

*nIDCaption*<br/>
IDENTIFICADOR del nombre que se va a colocar en la pestaña de esta página. Si es 0, el nombre se tomará de la plantilla de cuadro de diálogo de esta página.

*dwSize*<br/>
*lpszTemplateName* Apunta a una cadena que contiene el nombre de la plantilla para esta página. No puede ser nulo.

*nIDHeaderTitle*<br/>
IDENTIFICADOR del nombre que se va a colocar en la ubicación del título del encabezado de la página de propiedades.

*nIDHeaderSubTitle*<br/>
IDENTIFICADOR del nombre que se va a colocar en la ubicación del subtítulo del encabezado de la página de propiedades.

### <a name="remarks"></a>Comentarios

El objeto se muestra cuando se cumplen todas las condiciones siguientes:

- La página se ha agregado a una hoja de propiedades mediante [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Se ha llamado a la función [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) o [Create](../../mfc/reference/cpropertysheet-class.md#create) de la hoja de propiedades.

- El usuario ha seleccionado (con pestañas) esta página.

Si tiene varios parámetros (por ejemplo, si usa una matriz), use [CPropertySheet:: Construct](../../mfc/reference/cpropertysheet-class.md#construct) en lugar de `CPropertyPage`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>  CPropertyPage::GetPSP

Recupera la estructura [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) de Windows asociada `CPropertyPage` al objeto.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Valor devuelto

Referencia a la `PROPSHEETPAGE` estructura.

##  <a name="m_psp"></a>  CPropertyPage::m_psp

`m_psp`es una estructura cuyos miembros almacenan las características de [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Comentarios

Use esta estructura para inicializar la apariencia de una página de propiedades después de construirla.

Para obtener más información sobre esta estructura, incluida una lista de sus miembros, `PROPSHEETPAGE` vea en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>  CPropertyPage::OnApply

El marco de trabajo llama a esta función miembro cuando el usuario elige el botón Aceptar o aplicar ahora.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se aceptan los cambios; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Cuando el marco de trabajo llama a esta función, se aceptan los cambios realizados en todas las páginas de propiedades de la hoja de propiedades, la `OnApply` hoja de propiedades conserva el foco y devuelve true (el valor 1). Antes `OnApply` de que el marco de trabajo pueda llamarlo, debe haber llamado a [SetModified](#setmodified) y establecer su parámetro en true. Se activará el botón aplicar ahora en cuanto el usuario realice un cambio en la página de propiedades.

Invalide esta función miembro para especificar la acción que realizará el programa cuando el usuario haga clic en el botón aplicar ahora. Al reemplazar, la función debe devolver TRUE para aceptar los cambios y FALSE para evitar que los cambios surtan efecto.

La implementación predeterminada de `OnApply` llama `OnOK`a.

Para obtener más información acerca de los mensajes de notificación enviados cuando el usuario presiona el botón aplicar ahora o aceptar en una hoja de propiedades, consulte [PSN_APPLY](/windows/desktop/Controls/psn-apply) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage:: onok](#onok).

##  <a name="oncancel"></a>  CPropertyPage::OnCancel

El marco de trabajo llama a esta función miembro cuando se selecciona el botón Cancelar.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para realizar acciones de botón Cancelar. El valor predeterminado niega los cambios realizados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>  CPropertyPage::OnKillActive

El marco de trabajo llama a esta función miembro cuando la página ya no es la página activa.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si los datos se actualizaron correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para realizar tareas de validación de datos especiales.

La implementación predeterminada de esta función miembro copia la configuración de los controles de la página de propiedades en las variables miembro de la página de propiedades. Si los datos no se actualizaron correctamente debido a un error de validación de datos de diálogo (DDV), la página conserva el foco.

Después de que esta función miembro se devuelva correctamente, el marco de trabajo llamará a la función [onok](#onok) de la página.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>  CPropertyPage::OnOK

El marco de trabajo llama a esta función miembro cuando el usuario elige el botón Aceptar o aplicar ahora, inmediatamente después de que el marco de trabajo llame a [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Comentarios

Cuando el usuario elige el botón Aceptar o aplicar ahora, el marco de trabajo recibe la notificación [PSN_APPLY](/windows/desktop/Controls/psn-apply) de la página de propiedades. La llamada a `OnOK` no se realizará si se llama a [CPropertySheet::P ressbutton](../../mfc/reference/cpropertysheet-class.md#pressbutton) porque la página de propiedades no envía la notificación en ese caso.

Invalide esta función miembro para implementar un comportamiento adicional específico de la página activa actualmente cuando el usuario descarta toda la hoja de propiedades.

La implementación predeterminada de esta función miembro marca la página como "Clean" para reflejar que los datos se actualizaron en `OnKillActive` la función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel

El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón Cancelar y antes de que se realice la acción de cancelación.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE para evitar la operación de cancelación o TRUE para permitirlo.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para especificar una acción que el programa realiza cuando el usuario hace clic en el botón Cancelar.

La implementación predeterminada de `OnQueryCancel` devuelve true.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>  CPropertyPage::OnReset

El marco de trabajo llama a esta función miembro cuando el usuario elige el botón Cancelar.

```
virtual void OnReset();
```

### <a name="remarks"></a>Comentarios

Cuando el marco de trabajo llama a esta función, se descartan los cambios realizados en todas las páginas de propiedades realizadas por el usuario antes de elegir el botón aplicar ahora y la hoja de propiedades conserva el foco.

Invalide esta función miembro para especificar qué acción realiza el programa cuando el usuario hace clic en el botón Cancelar.

La implementación predeterminada de `OnReset` no hace nada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage:: OnCancel](#oncancel).

##  <a name="onsetactive"></a>  CPropertyPage::OnSetActive

El marco de trabajo llama a esta función miembro cuando el usuario elige la página y se convierte en la página activa.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la página se estableció correctamente activa; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para realizar tareas cuando se activa una página. La invalidación de esta función miembro normalmente llamaría a la versión predeterminada después de actualizar los miembros de datos, para permitirle actualizar los controles de página con los nuevos datos.

La implementación predeterminada crea la ventana de la página, si no se ha creado previamente, y la convierte en la página activa.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet:: SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

##  <a name="onwizardback"></a>  CPropertyPage::OnWizardBack

El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón atrás en un asistente.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Valor devuelto

0 para avanzar automáticamente a la página siguiente; -1 para evitar que la página cambie. Para saltar a una página que no sea la siguiente, devuelva el identificador del cuadro de diálogo que se va a mostrar.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón atrás.

Para obtener más información sobre cómo crear una hoja de propiedades de tipo asistente, vea [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>  CPropertyPage::OnWizardFinish

El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón Finalizar en un asistente.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se destruye cuando finaliza el asistente; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

Cuando un usuario hace clic en el botón **Finalizar** en un asistente, el marco de trabajo llama a esta función. Cuando `OnWizardFinish` devuelve true (un valor distinto de cero), la hoja de propiedades se puede destruir (pero no se destruye realmente). Llame `DestroyWindow` a para destruir la hoja de propiedades. No llame a `DestroyWindow` desde `OnWizardFinish`; si lo hace, se producirán daños en el montón u otros errores.

Puede invalidar esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón Finalizar. Al reemplazar esta función, devuelva FALSE para evitar que se destruya la hoja de propiedades.

Para obtener más información acerca de los mensajes de notificación enviados cuando el usuario presiona el botón Finalizar en una hoja de propiedades del asistente, vea [PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) en el Windows SDK.

Para obtener más información sobre cómo crear una hoja de propiedades de tipo asistente, vea [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>  CPropertyPage::OnWizardNext

El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón siguiente de un asistente.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Valor devuelto

0 para avanzar automáticamente a la página siguiente; -1 para evitar que la página cambie. Para saltar a una página que no sea la siguiente, devuelva el identificador del cuadro de diálogo que se va a mostrar.

### <a name="remarks"></a>Comentarios

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón siguiente.

Para obtener más información sobre cómo crear una hoja de propiedades de tipo asistente, vea [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>  CPropertyPage::QuerySiblings

Llame a esta función miembro para reenviar un mensaje a cada página de la hoja de propiedades.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*wParam*<br/>
Especifica información adicional dependiente del mensaje.

*lParam*<br/>
Especifica información adicional dependiente del mensaje

### <a name="return-value"></a>Valor devuelto

Valor distinto de cero de una página de la hoja de propiedades, o 0 si todas las páginas devuelven un valor de 0.

### <a name="remarks"></a>Comentarios

Si una página devuelve un valor distinto de cero, la hoja de propiedades no envía el mensaje a las páginas siguientes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>  CPropertyPage::SetModified

Llame a esta función miembro para habilitar o deshabilitar el botón aplicar ahora, en función de si la configuración de la página de propiedades se debe aplicar al objeto externo adecuado.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parámetros

*bChanged*<br/>
TRUE para indicar que la configuración de la página de propiedades se ha modificado desde la última vez que se aplicaron; FALSE para indicar que se ha aplicado la configuración de la página de propiedades o se debe omitir.

### <a name="remarks"></a>Comentarios

El marco de trabajo realiza un seguimiento de las páginas que están "desfasadas", es decir, las páginas de `SetModified( TRUE )`propiedades para las que se ha llamado. El botón aplicar ahora siempre estará habilitado si se llama `SetModified( TRUE )` a para una de las páginas. El botón aplicar ahora se deshabilitará cuando se `SetModified( FALSE )` llame a para una de las páginas, pero solo si ninguna de las otras páginas está "desfasada".

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
