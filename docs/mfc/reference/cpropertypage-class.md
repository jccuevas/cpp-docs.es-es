---
title: Clase CPropertyPage
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
ms.openlocfilehash: f46566eb562f1515e98aedf938ca68b225ee1b67
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751102"
---
# <a name="cpropertypage-class"></a>Clase CPropertyPage

Representa páginas individuales de una hoja de propiedades, también conocidas como cuadro de diálogo de pestaña.

## <a name="syntax"></a>Sintaxis

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|Construye un objeto `CPropertyPage`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPropertyPage::CancelToClose](#canceltoclose)|Cambia el botón Aceptar para leer Cerrar y deshabilita el botón Cancelar, después de un cambio irrecuperable en la página de una hoja de propiedades modal.|
|[CPropertyPage::Construct](#construct)|Construye un objeto `CPropertyPage`. Utilícelo `Construct` si desea especificar los parámetros en tiempo de ejecución o si está utilizando matrices.|
|[CPropertyPage::GetPSP](#getpsp)|Recupera la estructura [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) de `CPropertyPage` Windows asociada al objeto.|
|[CPropertyPage::OnApply](#onapply)|Llamado por el marco de trabajo cuando se hace clic en el botón Aplicar ahora.|
|[CPropertyPage::OnCancel](#oncancel)|Llamado por el marco de trabajo cuando se hace clic en el botón Cancelar.|
|[CPropertyPage::OnKillActive](#onkillactive)|Llamado por el marco de trabajo cuando la página actual ya no es la página activa. Realice la validación de datos aquí.|
|[CPropertyPage::OnOK](#onok)|Llamado por el marco de trabajo cuando se hace clic en el botón Aceptar, Aplicar ahora o Cerrar.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Llamado por el marco de trabajo cuando se hace clic en el botón Cancelar y antes de que se haya realizado la cancelación.|
|[CPropertyPage::OnReset](#onreset)|Llamado por el marco de trabajo cuando se hace clic en el botón Cancelar.|
|[CPropertyPage::OnSetActive](#onsetactive)|Llamado por el marco de trabajo cuando la página se hace la página activa.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Llamado por el marco de trabajo cuando se hace clic en el botón Atrás mientras se usa una hoja de propiedades de tipo asistente.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Llamado por el marco de trabajo cuando se hace clic en el botón Finalizar mientras se usa una hoja de propiedades de tipo asistente.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Llamado por el marco de trabajo cuando se hace clic en el botón Siguiente mientras se usa una hoja de propiedades de tipo asistente.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Reenvía el mensaje a cada página de la hoja de propiedades.|
|[CPropertyPage::SetModified](#setmodified)|Llame para activar o desactivar el botón Aplicar ahora.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|La estructura [PROPSHEETPAGE de](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) Windows. Proporciona acceso a los parámetros básicos de la página de propiedades.|

## <a name="remarks"></a>Observaciones

Al igual que con los cuadros de diálogo estándar, deriva una clase de `CPropertyPage` cada página de la hoja de propiedades. Para `CPropertyPage`usar objetos derivados, primero cree un [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) objeto y, a continuación, cree un objeto para cada página que va en la hoja de propiedades. Llame a [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) para cada página de la hoja y, a continuación, muestre la hoja de propiedades mediante una llamada a [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) para una hoja de propiedades modal o [CPropertySheet::Create](../../mfc/reference/cpropertysheet-class.md#create) para una hoja de propiedades no modal.

Puede crear un tipo de cuadro de diálogo de ficha denominado asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades que guían al usuario a través de los pasos de una operación, como la configuración de un dispositivo o la creación de un boletín informativo. En un cuadro de diálogo de ficha de tipo asistente, las páginas de propiedades no tienen pestañas y solo una página de propiedades está visible a la vez. Además, en lugar de tener los botones Aceptar y Aplicar ahora, un cuadro de diálogo de ficha de tipo asistente tiene un botón Atrás, un botón Siguiente o Finalizar y un botón Cancelar.

Para obtener más información sobre cómo establecer una hoja de propiedades como asistente, vea [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Para obtener más `CPropertyPage` información sobre el uso de objetos, vea el artículo Hojas de propiedades [y páginas](../../mfc/property-sheets-and-property-pages-in-mfc.md)de propiedades .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="cpropertypagecanceltoclose"></a><a name="canceltoclose"></a>CPropertyPage::CancelToClose

Llame a esta función después de que se haya realizado un cambio irrecuperable en los datos de una página de una hoja de propiedades modal.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Observaciones

Esta función cambiará el botón Aceptar a Cerrar y desactivará el botón Cancelar. Este cambio alerta al usuario de que un cambio es permanente y que las modificaciones no se pueden cancelar.

La `CancelToClose` función miembro no hace nada en una hoja de propiedades no esquemética, porque una hoja de propiedades no es mide no tiene un botón Cancelar de forma predeterminada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage::QuerySiblings](#querysiblings).

## <a name="cpropertypageconstruct"></a><a name="construct"></a>CPropertyPage::Construct

Llame a esta función miembro para construir un `CPropertyPage` objeto.

```cpp
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
ID de la plantilla utilizada para esta página.

*nIDCaption*<br/>
ID del nombre que se colocará en la pestaña de esta página. Si es 0, el nombre se tomará de la plantilla de cuadro de diálogo de esta página.

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla.

*nIDHeaderTitle*<br/>
ID del nombre que se colocará en la ubicación del título del encabezado de la página de propiedades. De forma predeterminada, 0.

*nIDHeaderSubTitle*<br/>
ID del nombre que se colocará en la ubicación de los subtítulos del encabezado de la página de propiedades. De forma predeterminada, 0.

### <a name="remarks"></a>Observaciones

El objeto se muestra después de cumplir todas las condiciones siguientes:

- La página se ha agregado a una hoja de propiedades mediante [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Se ha llamado a la función [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) o [Create](../../mfc/reference/cpropertysheet-class.md#create) de la hoja de propiedades.

- El usuario ha seleccionado (con pestañas para) esta página.

Llame `Construct` si no se ha llamado a uno de los otros constructores de clase. La `Construct` función miembro es flexible porque puede dejar la instrucción de parámetro en blanco y, a continuación, especificar varios parámetros y construcción en cualquier punto del código.

Debe usar `Construct` cuando trabaje con matrices y `Construct` debe llamar a cada miembro de la matriz para que a los miembros de datos se les asignen los valores adecuados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

## <a name="cpropertypagecpropertypage"></a><a name="cpropertypage"></a>CPropertyPage::CPropertyPage

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
ID de la plantilla utilizada para esta página.

*nIDCaption*<br/>
ID del nombre que se colocará en la pestaña de esta página. Si es 0, el nombre se tomará de la plantilla de cuadro de diálogo de esta página.

*dwSize*<br/>
*lpszTemplateName* Apunta a una cadena que contiene el nombre de la plantilla para esta página. No puede ser NULL.

*nIDHeaderTitle*<br/>
ID del nombre que se colocará en la ubicación del título del encabezado de la página de propiedades.

*nIDHeaderSubTitle*<br/>
ID del nombre que se colocará en la ubicación de los subtítulos del encabezado de la página de propiedades.

### <a name="remarks"></a>Observaciones

El objeto se muestra después de cumplir todas las condiciones siguientes:

- La página se ha agregado a una hoja de propiedades mediante [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Se ha llamado a la función [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) o [Create](../../mfc/reference/cpropertysheet-class.md#create) de la hoja de propiedades.

- El usuario ha seleccionado (con pestañas para) esta página.

Si tiene varios parámetros (por ejemplo, si utiliza una matriz), utilice `CPropertyPage` [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) en lugar de .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

## <a name="cpropertypagegetpsp"></a><a name="getpsp"></a>CPropertyPage::GetPSP

Recupera la estructura [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) de `CPropertyPage` Windows asociada al objeto.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Valor devuelto

Una referencia `PROPSHEETPAGE` a la estructura.

## <a name="cpropertypagem_psp"></a><a name="m_psp"></a>CPropertyPage::m_psp

`m_psp`es una estructura cuyos miembros almacenan las características de [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Observaciones

Utilice esta estructura para inicializar la apariencia de una página de propiedades después de construirla.

Para obtener más información sobre esta estructura, `PROPSHEETPAGE` incluida una lista de sus miembros, consulte el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

## <a name="cpropertypageonapply"></a><a name="onapply"></a>CPropertyPage::OnApply

El marco de trabajo llama a esta función miembro cuando el usuario elige el aceptar o el aplicar ahora botón.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se aceptan los cambios; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Cuando el marco de trabajo llama a esta función, se aceptan los cambios `OnApply` realizados en todas las páginas de propiedades de la hoja de propiedades, la hoja de propiedades conserva el foco y devuelve TRUE (el valor 1). Antes `OnApply` de que el marco de trabajo pueda llamar a ella, debe haber llamado a [SetModified](#setmodified) y establecer su parámetro en TRUE. Esto activará el botón Aplicar ahora tan pronto como el usuario realice un cambio en la página de propiedades.

Invalide esta función miembro para especificar qué acción realiza el programa cuando el usuario hace clic en el botón Aplicar ahora. Al reemplazar, la función debe devolver TRUE para aceptar cambios y FALSE para evitar que los cambios surtan efecto.

La implementación `OnApply` `OnOK`predeterminada de llamadas .

Para obtener más información acerca de los mensajes de notificación enviados cuando el usuario presiona el botón Aplicar ahora o Aceptar en una hoja de propiedades, consulte [PSN_APPLY](/windows/win32/Controls/psn-apply) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage::OnOK](#onok).

## <a name="cpropertypageoncancel"></a><a name="oncancel"></a>CPropertyPage::OnCancel

El marco de trabajo llama a esta función miembro cuando se selecciona el botón Cancelar.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Observaciones

Invalidar esta función miembro para realizar acciones de botón Cancelar. El valor predeterminado anula los cambios que se han realizado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

## <a name="cpropertypageonkillactive"></a><a name="onkillactive"></a>CPropertyPage::OnKillActive

El marco de trabajo llama a esta función miembro cuando la página ya no es la página activa.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos se actualizaron correctamente, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para realizar tareas especiales de validación de datos.

La implementación predeterminada de esta función miembro copia la configuración de los controles de la página de propiedades a las variables miembro de la página de propiedades. Si los datos no se actualizaron correctamente debido a un error de validación de datos de cuadro de diálogo (DDV), la página conserva el foco.

Después de que esta función miembro devuelve correctamente, el marco de trabajo llamará a la función [OnOK](#onok) de la página.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

## <a name="cpropertypageonok"></a><a name="onok"></a>CPropertyPage::OnOK

El marco de trabajo llama a esta función miembro cuando el usuario elige el botón Aceptar o Aplicar ahora, inmediatamente después de que el marco de trabajo llame a [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Observaciones

Cuando el usuario elige el Aceptar o el botón Aplicar ahora, el marco de trabajo recibe la [notificación PSN_APPLY](/windows/win32/Controls/psn-apply) de la página de propiedades. La llamada `OnOK` a no se realizará si se llama a [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) porque la página de propiedades no envía la notificación en ese caso.

Invalidar esta función miembro para implementar un comportamiento adicional específico de la página activa actualmente cuando el usuario descarta toda la hoja de propiedades.

La implementación predeterminada de esta función miembro marca la página como `OnKillActive` "limpia" para reflejar que los datos se actualizaron en la función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

## <a name="cpropertypageonquerycancel"></a><a name="onquerycancel"></a>CPropertyPage::OnQueryCancel

El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón Cancelar y antes de que se haya realizado la acción de cancelación.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE para evitar la operación de cancelación o TRUE para permitirlo.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para especificar una acción que el programa realiza cuando el usuario hace clic en el botón Cancelar.

La implementación `OnQueryCancel` predeterminada de devuelve TRUE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

## <a name="cpropertypageonreset"></a><a name="onreset"></a>CPropertyPage::OnReset

El marco de trabajo llama a esta función miembro cuando el usuario elige el botón Cancelar.

```
virtual void OnReset();
```

### <a name="remarks"></a>Observaciones

Cuando el marco de trabajo llama a esta función, se descartan los cambios en todas las páginas de propiedades realizadas por el usuario que eligieron previamente el botón Aplicar ahora y la hoja de propiedades conserva el foco.

Invalide esta función miembro para especificar qué acción realiza el programa cuando el usuario hace clic en el botón Cancelar.

La implementación `OnReset` predeterminada de no hace nada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertyPage::OnCancel](#oncancel).

## <a name="cpropertypageonsetactive"></a><a name="onsetactive"></a>CPropertyPage::OnSetActive

El marco de trabajo llama a esta función miembro cuando el usuario elige la página y se convierte en la página activa.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la página se estableció correctamente activa; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para realizar tareas cuando se activa una página. La invalidación de esta función miembro normalmente llamaría a la versión predeterminada después de actualizar los miembros de datos, para permitirle actualizar los controles de página con los nuevos datos.

La implementación predeterminada crea la ventana para la página, si no se creó anteriormente, y la convierte en la página activa.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

## <a name="cpropertypageonwizardback"></a><a name="onwizardback"></a>CPropertyPage::OnWizardBack

El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón Atrás de un asistente.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Valor devuelto

0 para avanzar automáticamente a la página siguiente; -1 para evitar que la página cambie. Para saltar a una página que no sea la siguiente, devuelva el identificador del cuadro de diálogo que se va a mostrar.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón Atrás.

Para obtener más información sobre cómo crear una hoja de propiedades de tipo asistente, vea [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

## <a name="cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish

El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón Finalizar de un asistente.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se destruye cuando finaliza el asistente; de lo contrario cero.

### <a name="remarks"></a>Observaciones

Cuando un usuario hace clic en **el** finalizar botón en un asistente, el marco de trabajo llama a esta función; cuando `OnWizardFinish` devuelve TRUE (un valor distinto de cero), la hoja de propiedades puede destruirse (pero no se destruye realmente). Llame `DestroyWindow` para destruir la hoja de propiedades. No llame `DestroyWindow` `OnWizardFinish`desde ; hacerlo causará daños en el montón u otros errores.

Puede invalidar esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón Finalizar. Al reemplazar esta función, devuelva FALSE para evitar que se destruya la hoja de propiedades.

Para obtener más información acerca de los mensajes de notificación enviados cuando el usuario presiona el botón Finalizar en una hoja de propiedades del asistente, vea [PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) en el Windows SDK.

Para obtener más información sobre cómo crear una hoja de propiedades de tipo asistente, vea [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

## <a name="cpropertypageonwizardnext"></a><a name="onwizardnext"></a>CPropertyPage::OnWizardNext

El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón Siguiente de un asistente.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Valor devuelto

0 para avanzar automáticamente a la página siguiente; -1 para evitar que la página cambie. Para saltar a una página que no sea la siguiente, devuelva el identificador del cuadro de diálogo que se va a mostrar.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para especificar alguna acción que el usuario debe realizar cuando se presiona el botón Siguiente.

Para obtener más información sobre cómo crear una hoja de propiedades de tipo asistente, vea [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

## <a name="cpropertypagequerysiblings"></a><a name="querysiblings"></a>CPropertyPage::QuerySiblings

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

El valor distinto de cero de una página de la hoja de propiedades, o 0 si todas las páginas devuelven un valor de 0.

### <a name="remarks"></a>Observaciones

Si una página devuelve un valor distinto de cero, la hoja de propiedades no envía el mensaje a las páginas posteriores.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

## <a name="cpropertypagesetmodified"></a><a name="setmodified"></a>CPropertyPage::SetModified

Llame a esta función miembro para habilitar o deshabilitar el botón Aplicar ahora, en función de si la configuración de la página de propiedades se debe aplicar al objeto externo adecuado.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parámetros

*bChanged*<br/>
TRUE para indicar que la configuración de la página de propiedades se ha modificado desde la última vez que se aplicaron; FALSE para indicar que se ha aplicado la configuración de la página de propiedades o se debe omitir.

### <a name="remarks"></a>Observaciones

El marco de trabajo realiza un seguimiento de qué páginas son `SetModified( TRUE )`"sucias", es decir, las páginas de propiedades para las que ha llamado . El botón Aplicar ahora siempre estará `SetModified( TRUE )` habilitado si llama a una de las páginas. El botón Aplicar ahora se `SetModified( FALSE )` deshabilitará cuando llame a una de las páginas, pero solo si ninguna de las otras páginas está "sucia".

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo cmNCTRL2 de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[EJEMPLO de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)
