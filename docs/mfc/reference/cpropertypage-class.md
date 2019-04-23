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
ms.openlocfilehash: 9d4100037c5a6cd2eeef1a50fb2d5a46b2cb6505
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772728"
---
# <a name="cpropertypage-class"></a>CPropertyPage (clase)

Representa páginas individuales de una hoja de propiedades, también conocidas como cuadro de diálogo de pestaña.

## <a name="syntax"></a>Sintaxis

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|Construye un objeto `CPropertyPage`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPropertyPage::CancelToClose](#canceltoclose)|Cambia el botón Aceptar para cerrar de lectura y deshabilita el botón Cancelar, tras un cambio en la página de una hoja de propiedades modal irrecuperable.|
|[CPropertyPage::Construct](#construct)|Construye un objeto `CPropertyPage`. Use `Construct` si desea especificar los parámetros en tiempo de ejecución, o si está utilizando matrices.|
|[CPropertyPage::GetPSP](#getpsp)|Recupera el Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) estructura asociada con el `CPropertyPage` objeto.|
|[CPropertyPage::OnApply](#onapply)|Lo llama el marco de trabajo cuando se hace clic en el botón Aplicar ahora.|
|[CPropertyPage::OnCancel](#oncancel)|Lo llama el marco de trabajo cuando se hace clic en el botón Cancelar.|
|[CPropertyPage::OnKillActive](#onkillactive)|Lo llama el marco de trabajo cuando la página actual ya no es la página activa. Realizar la validación de datos aquí.|
|[CPropertyPage::OnOK](#onok)|Lo llama el marco de trabajo cuando se hace clic en el Aceptar, aplicar ahora o botón de cierre.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Lo llama el marco de trabajo cuando se hace clic en el botón Cancelar, y antes de que la cancelación ha tenido lugar.|
|[CPropertyPage::OnReset](#onreset)|Lo llama el marco de trabajo cuando se hace clic en el botón Cancelar.|
|[CPropertyPage::OnSetActive](#onsetactive)|Lo llama el marco de trabajo cuando la página se convierte en la página activa.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Lo llama el marco de trabajo cuando se hace clic en el botón Atrás mientras se usa una hoja de propiedades de tipo asistente.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Lo llama el marco de trabajo cuando se hace clic en el botón Finalizar al utilizar una hoja de propiedades de tipo asistente.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Lo llama el marco de trabajo cuando se hace clic en el botón siguiente mientras se usa una hoja de propiedades de tipo asistente.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Reenvía el mensaje a cada página de la hoja de propiedades.|
|[CPropertyPage::SetModified](#setmodified)|Llamada a activar o desactivar el botón Aplicar ahora.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|El Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) estructura. Proporciona acceso a los parámetros de la página de propiedad básico.|

## <a name="remarks"></a>Comentarios

Como con cuadros de diálogo estándar, deriva una clase de `CPropertyPage` para cada página en la hoja de propiedades. Para usar `CPropertyPage`-objetos derivados, cree primero un [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) objeto y, a continuación, cree un objeto para cada página que se incluye en la hoja de propiedades. Llame a [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) para cada página en la hoja y, a continuación, muestre la hoja de propiedades mediante una llamada a [CPropertySheet:: DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) para una hoja de propiedades modal o [CPropertySheet:: Crear](../../mfc/reference/cpropertysheet-class.md#create) para una hoja de propiedades no modal.

Puede crear un tipo de ficha del cuadro de diálogo llama a un asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades que guían al usuario a través de los pasos necesarios para una operación, como la configuración de un dispositivo o la creación de un boletín. En un cuadro de diálogo de pestaña de tipo asistente las páginas de propiedades no tiene pestañas y solo una página de propiedades es visible a la vez. Además, en lugar de tener los botones Aceptar y aplicar ahora, un cuadro de diálogo de pestaña de tipo asistente tiene un botón Atrás, un botón siguiente o finalizar y un botón Cancelar.

Para obtener más información acerca de cómo establecer una hoja de propiedades como un asistente, consulte [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Para obtener más información sobre el uso de `CPropertyPage` objetos, consulte el artículo [hojas de propiedades y páginas de propiedades](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

##  <a name="canceltoclose"></a>  CPropertyPage::CancelToClose

Llame a esta función después de que se ha realizado un cambio irrecuperable a los datos en una página de una hoja de propiedades modal.

```
void CancelToClose();
```

### <a name="remarks"></a>Comentarios

Esta función cambiará el botón Aceptar para cerrar y deshabilitar el botón Cancelar. Este cambio no se puede cancelar el usuario que un cambio es permanente y las modificaciones de las alertas.

El `CancelToClose` función miembro no hace nada en una hoja de propiedades no modal, porque una hoja de propiedades no modal no tiene un botón Cancelar de forma predeterminada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage::QuerySiblings](#querysiblings).

##  <a name="construct"></a>  CPropertyPage::Construct

Llame a esta función miembro para construir un `CPropertyPage` objeto.

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
Id. de la plantilla usada para esta página.

*nIDCaption*<br/>
Identificador del nombre que se colocarán en la ficha para esta página. Si es 0, se realizará el nombre de la plantilla de cuadro de diálogo para esta página.

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla.

*nIDHeaderTitle*<br/>
Identificador del nombre que se colocarán en la ubicación del encabezado de página de propiedades del título. De forma predeterminada, es 0.

*nIDHeaderSubTitle*<br/>
Identificador del nombre que se colocarán en la ubicación de subtítulo del encabezado de página de propiedad. De forma predeterminada, es 0.

### <a name="remarks"></a>Comentarios

El objeto se muestra después de que se cumplen todas las condiciones siguientes:

- La página se ha agregado a una hoja de propiedades mediante [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- La hoja de propiedades [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) o [crear](../../mfc/reference/cpropertysheet-class.md#create) se ha llamado la función.

- El usuario ha seleccionado (mediante el tabulador) esta página.

Llamar a `Construct` si uno de los otros constructores de clase no se ha llamado. El `Construct` función miembro es flexible porque puede dejar en blanco la declaración de parámetro y, a continuación, especificar varios parámetros y la construcción en cualquier momento en el código.

Debe usar `Construct` cuando se trabaja con matrices, y es preciso llamar `Construct` para cada miembro de la matriz para que los miembros de datos se asignan los valores adecuados.

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
Id. de la plantilla usada para esta página.

*nIDCaption*<br/>
Identificador del nombre que se colocarán en la ficha para esta página. Si es 0, se realizará el nombre de la plantilla de cuadro de diálogo para esta página.

*dwSize*<br/>
*lpszTemplateName* señala a una cadena que contiene el nombre de la plantilla para esta página. No puede ser nulo.

*nIDHeaderTitle*<br/>
Identificador del nombre que se colocarán en la ubicación del encabezado de página de propiedades del título.

*nIDHeaderSubTitle*<br/>
Identificador del nombre que se colocarán en la ubicación de subtítulo del encabezado de página de propiedad.

### <a name="remarks"></a>Comentarios

El objeto se muestra después de que se cumplen todas las condiciones siguientes:

- La página se ha agregado a una hoja de propiedades mediante [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- La hoja de propiedades [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) o [crear](../../mfc/reference/cpropertysheet-class.md#create) se ha llamado la función.

- El usuario ha seleccionado (mediante el tabulador) esta página.

Si tiene varios parámetros (por ejemplo, si está utilizando una matriz), use [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) en lugar de `CPropertyPage`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>  CPropertyPage::GetPSP

Recupera el Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) estructura asociada con el `CPropertyPage` objeto.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a la `PROPSHEETPAGE` estructura.

##  <a name="m_psp"></a>  CPropertyPage::m_psp

`m_psp` es una estructura cuyos miembros almacenan las características de [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Comentarios

Utilice esta estructura para inicializar la apariencia de una página de propiedades después de se construye.

Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea `PROPSHEETPAGE` en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>  CPropertyPage::OnApply

Esta función miembro se llama el marco de trabajo cuando el usuario elige Aceptar o en el botón Aplicar ahora.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se aceptan los cambios; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Cuando el marco llama a esta función, se aceptan los cambios realizados en todas las páginas de propiedades en la hoja de propiedades, la hoja de propiedades conserva el foco, y `OnApply` devuelve TRUE (el valor 1). Antes de `OnApply` se puede llamar el marco de trabajo, debe haber llamado a [SetModified](#setmodified) y establezca su parámetro en TRUE. Esto activará el botón Aplicar ahora tan pronto como el usuario realiza un cambio en la página de propiedades.

Reemplace esta función miembro para especificar qué acción realizada por el programa cuando el usuario hace clic en el botón Aplicar ahora. Cuando se reemplaza, la función debe devolver TRUE para aceptar los cambios y FALSE para impedir que los cambios surtan efecto.

La implementación predeterminada de `OnApply` llamadas `OnOK`.

Para obtener más información acerca de los mensajes de notificación se envía cuando el usuario presiona el aplicar ahora o botón Aceptar en una hoja de propiedades, vea [PSN_APPLY](/windows/desktop/Controls/psn-apply) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage::OnOK](#onok).

##  <a name="oncancel"></a>  CPropertyPage::OnCancel

Esta función miembro se llama el marco de trabajo cuando se selecciona el botón Cancelar.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para llevar a cabo acciones de botón de cancelación. El valor predeterminado niega los cambios que se han realizado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>  CPropertyPage::OnKillActive

Esta función miembro se llama el marco de trabajo cuando la página ya no es la página activa.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos se actualizan correctamente, si no 0.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para llevar a cabo las tareas de validación de datos especiales.

La implementación predeterminada de esta función miembro copia la configuración de los controles en la página de propiedades a las variables de miembro de la página de propiedades. Si los datos no se actualizan correctamente debido a un error de validación (DDV) de datos de cuadro de diálogo, la página conserva el foco.

Después de esta función miembro devuelve correctamente, el marco de trabajo llamará a la página [OnOK](#onok) función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>  CPropertyPage::OnOK

Esta función miembro se llama el marco de trabajo cuando el usuario elige Aceptar o en el botón Aplicar ahora, inmediatamente después de las llamadas de framework [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Comentarios

Cuando el usuario elige Aceptar o en el botón Aplicar ahora, el marco de trabajo recibe el [PSN_APPLY](/windows/desktop/Controls/psn-apply) notificación desde la página de propiedades. La llamada a `OnOK` no se realizará si se llama a [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) porque la página de propiedades no envía la notificación en ese caso.

Reemplace esta función miembro para implementar el comportamiento adicional específico de la página actualmente activa cuando el usuario cierra la hoja de propiedades completa.

La implementación predeterminada de esta función miembro marca como "limpiar" para reflejar que los datos se actualizan en la página de la `OnKillActive` función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel

Esta función miembro se llama el marco de trabajo cuando el usuario hace clic en el botón Cancelar y antes de la cancelación ha tomado una acción.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE para permitirla o FALSE para impedir que la operación de cancelación.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para especificar una acción realizada por el programa cuando el usuario hace clic en el botón Cancelar.

La implementación predeterminada de `OnQueryCancel` devuelve TRUE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>  CPropertyPage::OnReset

Esta función miembro se llama el marco de trabajo cuando el usuario elige el botón Cancelar.

```
virtual void OnReset();
```

### <a name="remarks"></a>Comentarios

Cuando el marco llama a esta función, se descartan los cambios realizados en todas las páginas de propiedades que se han realizado por el usuario anteriormente seleccionando el botón Aplicar ahora y la hoja de propiedades conserva el foco.

Reemplace esta función miembro para especificar qué acción realizada por el programa cuando el usuario hace clic en el botón Cancelar.

La implementación predeterminada de `OnReset` no hace nada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage::OnCancel](#oncancel).

##  <a name="onsetactive"></a>  CPropertyPage::OnSetActive

Esta función miembro se llama el marco de trabajo cuando la página elegida por el usuario y se convierte en la página activa.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la página se estableció correctamente active; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para llevar a cabo las tareas cuando se activa una página. La invalidación de esta función miembro normalmente llamaría a la versión predeterminada después de actualizar los miembros de datos, para que permita actualizar los controles de página con los nuevos datos.

La implementación predeterminada crea la ventana de la página, si no ha creado anteriormente y facilita la página activa.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

##  <a name="onwizardback"></a>  CPropertyPage::OnWizardBack

Esta función miembro se llama el marco de trabajo cuando el usuario hace clic en el botón Atrás en un asistente.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Valor devuelto

0 para pasar automáticamente a la página siguiente; -1 para impedir que cambien la página. Para saltar a una página distinta de la siguiente, devolver el identificador del cuadro de diálogo que se mostrará.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón Atrás.

Para obtener más información sobre cómo realizar una hoja de propiedades de tipo asistente, consulte [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>  CPropertyPage::OnWizardFinish

Esta función miembro se llama el marco de trabajo cuando el usuario hace clic en el botón Finalizar en un asistente.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se destruye cuando finalice el Asistente; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Cuando un usuario hace clic en el **finalizar** botón en un asistente, el marco de trabajo llama a esta función; cuando `OnWizardFinish` devuelve TRUE (valor distinto de cero), la hoja de propiedades es capaz de destruirse (pero no se destruye realmente). Llame a `DestroyWindow` para destruir la hoja de propiedades. No llame a `DestroyWindow` desde `OnWizardFinish`; Esto hará que otros errores o daños en el montón.

Puede reemplazar esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón Finalizar. Al reemplazar esta función, devuelve FALSE para impedir que se está destruyendo la hoja de propiedades.

Para obtener más información acerca de los mensajes de notificación se envía cuando el usuario presiona el botón Finalizar en una hoja de propiedades del asistente, consulte [PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) en el SDK de Windows.

Para obtener más información sobre cómo realizar una hoja de propiedades de tipo asistente, consulte [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>  CPropertyPage::OnWizardNext

Esta función miembro se llama el marco de trabajo cuando el usuario hace clic en el botón siguiente en un asistente.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Valor devuelto

0 para pasar automáticamente a la página siguiente; -1 para impedir que cambien la página. Para saltar a una página distinta de la siguiente, devolver el identificador del cuadro de diálogo que se mostrará.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón siguiente.

Para obtener más información sobre cómo realizar una hoja de propiedades de tipo asistente, consulte [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>  CPropertyPage::QuerySiblings

Llame a esta función miembro para reenviar un mensaje a cada página en la hoja de propiedades.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*wParam*<br/>
Especifica información adicional de dependiente del mensaje.

*lParam*<br/>
Especifica información adicional de dependiente de mensaje

### <a name="return-value"></a>Valor devuelto

El valor distinto de cero de una página en la hoja de propiedades, o 0 si todas las páginas de devuelven un valor de 0.

### <a name="remarks"></a>Comentarios

Si una página, devuelve un valor distinto de cero, la hoja de propiedades no envía el mensaje a las páginas siguientes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>  CPropertyPage::SetModified

Llame a esta función miembro para habilitar o deshabilitar el botón Aplicar ahora, en función de si se debe aplicar la configuración en la página de propiedades en el objeto externo adecuado.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parámetros

*bChanged*<br/>
TRUE para indicar que la configuración de la página de propiedades se han modificado desde la última vez que se aplicaron; FALSE para indicar que la configuración de la página de propiedades se han aplicado o que debe omitirse.

### <a name="remarks"></a>Comentarios

El marco de trabajo realiza el seguimiento de las páginas son "sucios", es decir, páginas de propiedades para el que ha llamado `SetModified( TRUE )`. Siempre se habilitará el botón Aplicar ahora si se llama a `SetModified( TRUE )` para una de las páginas. Se deshabilitará el botón Aplicar ahora al llamar a `SetModified( FALSE )` para una de las páginas, pero sólo si ninguna de las otras páginas está "sucio".

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Vea también

[MFC Sample CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC Sample CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo SNAPVW de MFC](../../overview/visual-cpp-samples.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
