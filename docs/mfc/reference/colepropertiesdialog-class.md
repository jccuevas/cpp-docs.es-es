---
title: Clase COlePropertiesDialog
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: b819bc430868717a2df01a086b482dfe6d56cc0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504163"
---
# <a name="colepropertiesdialog-class"></a>Clase COlePropertiesDialog

Encapsula el cuadro de diálogo Propiedades de objeto de OLE común de Windows.

## <a name="syntax"></a>Sintaxis

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Construye un objeto `COlePropertiesDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Lo llama el marco de trabajo cuando cambia el escalado del elemento de documento.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Estructura que se usa para inicializar la página "general" `COlePropertiesDialog` de un objeto.|
|[COlePropertiesDialog::m_lp](#m_lp)|Estructura que se usa para inicializar la página de "vínculo `COlePropertiesDialog` " de un objeto.|
|[COlePropertiesDialog::m_op](#m_op)|Estructura que se usa para inicializar el `COlePropertiesDialog` objeto.|
|[COlePropertiesDialog::m_psh](#m_psh)|Estructura que se usa para agregar páginas de propiedades personalizadas adicionales.|
|[COlePropertiesDialog::m_vp](#m_vp)|Estructura que se usa para personalizar la página de "vista" `COlePropertiesDialog` de un objeto.|

## <a name="remarks"></a>Comentarios

Los cuadros de diálogo de propiedades de objetos OLE comunes proporcionan una manera sencilla de mostrar y modificar las propiedades de un elemento de documento OLE de una manera coherente con los estándares de Windows. Estas propiedades incluyen, entre otras, información sobre el archivo representado por el elemento de documento, opciones para mostrar el escalado de iconos e imágenes e información sobre el vínculo del elemento (si el elemento está vinculado).

Para usar un `COlePropertiesDialog` objeto, primero cree el objeto mediante el `COlePropertiesDialog` constructor. Una vez construido el cuadro de diálogo, llame a `DoModal` la función miembro para mostrar el cuadro de diálogo y permitir que el usuario modifique las propiedades del elemento. `DoModal`Devuelve si el usuario seleccionó el botón Aceptar (IDOK) o cancelar (IDCANCEL). Además de los botones aceptar y cancelar, hay un botón aplicar. Cuando el usuario selecciona aplicar, los cambios realizados en las propiedades del elemento de documento se aplican al elemento y su imagen se actualiza automáticamente, pero permanece activa.

El miembro de datos [m_psh](#m_psh) es un puntero a `PROPSHEETHEADER` una estructura y, en la mayoría de los casos, no necesitará tener acceso a él explícitamente. Una excepción es cuando se necesitan páginas de propiedades adicionales además de las páginas generales, de vista y de vínculo predeterminadas. En este caso, puede modificar el `m_psh` miembro de datos para incluir las páginas personalizadas antes de llamar a la `DoModal` función miembro.

Para obtener más información sobre los cuadros de diálogo OLE, vea los [cuadros de diálogo de los artículos en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs. h

##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog

Crea un objeto `COlePropertiesDialog`.

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento cuyas propiedades se están accediendo.

*nScaleMin*<br/>
Porcentaje mínimo de escala para la imagen del elemento de documento.

*nScaleMax*<br/>
Porcentaje de escalado máximo para la imagen de elemento de documento.

*pParentWnd*<br/>
Puntero al elemento primario o propietario del cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Derive la clase de cuadro de diálogo de propiedades `COlePropertiesDialog` de objetos OLE comunes de para implementar el escalado de los elementos de documento. Los cuadros de diálogo implementados por una instancia de esta clase no admiten el escalado del elemento de documento.

De forma predeterminada, el cuadro de diálogo Propiedades de objeto OLE comunes tiene tres páginas predeterminadas:

- General

   Esta página contiene información del sistema para el archivo representado por el elemento de documento seleccionado. Desde esta página, el usuario puede convertir el elemento seleccionado en otro tipo.

- Ver

   Esta página contiene opciones para mostrar el elemento, cambiar el icono y cambiar el escalado de la imagen.

- Link

   Esta página contiene opciones para cambiar la ubicación del elemento vinculado y actualizar el elemento vinculado. Desde esta página, el usuario puede romper el vínculo del elemento seleccionado.

Para agregar páginas más allá de las que se proporcionan de forma predeterminada, modifique la variable miembro [m_psh](#m_psh) antes de `COlePropertiesDialog`salir del constructor de la clase derivada de. Se trata de una implementación avanzada del `COlePropertiesDialog` constructor.

##  <a name="domodal"></a>  COlePropertiesDialog::DoModal

Llame a esta función miembro para mostrar el cuadro de diálogo Propiedades comunes del objeto OLE de Windows y permitir que el usuario vea y/o cambie las distintas propiedades del elemento de documento.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL si se realiza correctamente; de lo contrario, es 0. IDOK y IDCANCEL son constantes que indican si el usuario seleccionó el botón Aceptar o cancelar.

Si se devuelve IDCANCEL, puede llamar a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

Estructura de tipo [OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw), que se usa para inicializar la página general del cuadro de diálogo Propiedades de objeto OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Comentarios

Esta página muestra el tipo y el tamaño de una incrustación y permite que el usuario tenga acceso al cuadro de diálogo convertir. En esta página también se muestra el destino del vínculo si el objeto es un vínculo.

Para obtener más información sobre `OLEUIGNRLPROPS` la estructura, vea el Windows SDK.

##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp

Estructura de tipo [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw), que se usa para inicializar la página de vínculo del cuadro de diálogo Propiedades de objeto OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Comentarios

Esta página muestra la ubicación del elemento vinculado y permite que el usuario actualice, o interrumpa, el vínculo al elemento.

Para obtener más información sobre `OLEUILINKPROPS` la estructura, vea el Windows SDK.

##  <a name="m_op"></a>  COlePropertiesDialog::m_op

Estructura de tipo [OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw), que se usa para inicializar el cuadro de diálogo Propiedades comunes del objeto OLE.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Comentarios

Esta estructura contiene miembros que se utilizan para inicializar las páginas general, de vínculo y de vista.

Para obtener más información, vea las estructuras OLEUIOBJECTPROPS y [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw) en el Windows SDK.

##  <a name="m_psh"></a>COlePropertiesDialog::m_psh

Estructura de tipo [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2), cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Comentarios

Después de construir un `COlePropertiesDialog` objeto, puede utilizar `m_psh` para establecer diversos aspectos del cuadro de diálogo antes de llamar a `DoModal` la función miembro.

Si modifica el miembro `m_psh` de datos directamente, invalidará el comportamiento predeterminado.

Para obtener más información sobre `PROPSHEETHEADER` la estructura, vea el Windows SDK.

##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp

Estructura de tipo [OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw), que se usa para inicializar la página de vista del cuadro de diálogo Propiedades de objeto OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Comentarios

Esta página permite al usuario alternar entre las vistas "contenido" y "icónica" del objeto y cambiar su escala en el contenedor. También permite al usuario tener acceso al cuadro de diálogo Cambiar icono cuando el objeto se muestra como un icono.

Para obtener más información sobre `OLEUIVIEWPROPS` la estructura, vea el Windows SDK.

##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale

Lo llama el marco de trabajo cuando el valor de escalado ha cambiado y se ha seleccionado aceptar o aplicar.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento cuyas propiedades se están accediendo.

*nCurrentScale*<br/>
Valor numérico de la escala del cuadro de diálogo.

*bRelativeToOrig*<br/>
Indica si el ajuste de escala se aplica al tamaño original del elemento de documento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controla; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada no hace nada. Debe reemplazar esta función para habilitar los controles de escalado.

> [!NOTE]
>  Antes de que se muestre el cuadro de diálogo Propiedades comunes del objeto OLE, el marco de trabajo llama a esta función con un valor NULL para *pItem* y a-1 para *nCurrentScale*. Esto se hace para determinar si se deben habilitar los controles de escalado.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage (clase)](../../mfc/reference/cpropertypage-class.md)
