---
title: COlePropertiesDialog (clase)
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
ms.openlocfilehash: f065894ff49af755ab4020f71b0213b19db49054
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374898"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog (clase)

Encapsula el cuadro de diálogo Propiedades de objeto de OLE común de Windows.

## <a name="syntax"></a>Sintaxis

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Construye un objeto `COlePropertiesDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Llamado por el marco de trabajo cuando el escalado del elemento de documento ha cambiado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Estructura utilizada para inicializar la página `COlePropertiesDialog` "General" de un objeto.|
|[COlePropertiesDialog::m_lp](#m_lp)|Estructura utilizada para inicializar la página `COlePropertiesDialog` "Link" de un objeto.|
|[COlePropertiesDialog::m_op](#m_op)|Estructura utilizada para `COlePropertiesDialog` inicializar el objeto.|
|[COlePropertiesDialog::m_psh](#m_psh)|Estructura utilizada para agregar páginas de propiedades personalizadas adicionales.|
|[COlePropertiesDialog::m_vp](#m_vp)|Estructura utilizada para personalizar la página `COlePropertiesDialog` "Ver" de un objeto.|

## <a name="remarks"></a>Observaciones

Los cuadros de diálogo Propiedades de objeto Sole comunes proporcionan una manera sencilla de mostrar y modificar las propiedades de un elemento de documento OLE de una manera coherente con los estándares de Windows. Estas propiedades incluyen, entre otras, información sobre el archivo representado por el elemento de documento, opciones para mostrar el icono y la escala de la imagen e información sobre el vínculo del elemento (si el elemento está vinculado).

Para utilizar `COlePropertiesDialog` un objeto, primero `COlePropertiesDialog` cree el objeto mediante el constructor. Una vez construido el cuadro de `DoModal` diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir al usuario modificar las propiedades del elemento. `DoModal`devuelve si el usuario ha seleccionado el botón Aceptar (IDOK) o Cancelar (IDCANCEL). Además de los botones Aceptar y Cancelar, hay un botón Aplicar. Cuando el usuario selecciona Aplicar, los cambios realizados en las propiedades del elemento de documento se aplican al elemento y su imagen se actualiza automáticamente, pero permanece activa.

El [m_psh](#m_psh) miembro de datos `PROPSHEETHEADER` es un puntero a una estructura y, en la mayoría de los casos, no necesitará tener acceso a ella explícitamente. Una excepción es cuando necesita páginas de propiedades adicionales más allá de las páginas General, Ver y Vínculo predeterminadas. En este caso, puede `m_psh` modificar el miembro de datos `DoModal` para incluir las páginas personalizadas antes de llamar a la función miembro.

Para obtener más información sobre los cuadros de diálogo OLE, vea el artículo [Cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="colepropertiesdialogcolepropertiesdialog"></a><a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

Crea un objeto `COlePropertiesDialog` .

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento a cuyas propiedades se tiene acceso.

*nScaleMin*<br/>
Porcentaje de escala mínimo para la imagen del elemento de documento.

*nScaleMax*<br/>
Porcentaje máximo de escala para la imagen del elemento de documento.

*pParentWnd*<br/>
Puntero al elemento primario o propietario del cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Derive la clase de cuadro `COlePropertiesDialog` de diálogo Propiedades de objeto OLE común para implementar el escalado para los elementos de documento. Los cuadros de diálogo implementados por una instancia de esta clase no admitirán el escalado del elemento de documento.

De forma predeterminada, el cuadro de diálogo Propiedades de objeto OLE común tiene tres páginas predeterminadas:

- General

   Esta página contiene información del sistema para el archivo representado por la posición de documento seleccionada. Desde esta página, el usuario puede convertir el elemento seleccionado a otro tipo.

- Ver

   Esta página contiene opciones para mostrar el elemento, cambiar el icono y cambiar la escala de la imagen.

- Vínculo

   Esta página contiene opciones para cambiar la ubicación del elemento vinculado y actualizar el elemento vinculado. Desde esta página, el usuario puede romper el vínculo del elemento seleccionado.

Para agregar páginas más allá [m_psh](#m_psh) de las proporcionadas de forma `COlePropertiesDialog`predeterminada, modifique la m_psh variable miembro antes de salir del constructor de la clase derivada. Se trata de una `COlePropertiesDialog` implementación avanzada del constructor.

## <a name="colepropertiesdialogdomodal"></a><a name="domodal"></a>COlePropertiesDialog::DoModal

Llame a esta función miembro para mostrar el cuadro de diálogo Propiedades de objeto OLE comunes de Windows y permitir al usuario ver o cambiar las distintas propiedades del elemento de documento.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL si se realiza correctamente; de lo contrario 0. IDOK e IDCANCEL son constantes que indican si el usuario ha seleccionado el botón Aceptar o Cancelar.

Si se devuelve IDCANCEL, puede llamar a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

## <a name="colepropertiesdialogm_gp"></a><a name="m_gp"></a>COlePropertiesDialog::m_gp

Estructura de tipo [OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw), que se utiliza para inicializar la página General del cuadro de diálogo Propiedades de objeto OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Observaciones

Esta página muestra el tipo y el tamaño de una incrustación y permite al usuario acceder al cuadro de diálogo Convertir. Esta página también muestra el destino del vínculo si el objeto es un vínculo.

Para obtener más `OLEUIGNRLPROPS` información sobre la estructura, consulte el Windows SDK.

## <a name="colepropertiesdialogm_lp"></a><a name="m_lp"></a>COlePropertiesDialog::m_lp

Estructura de tipo [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw), que se utiliza para inicializar la página Vínculo del cuadro de diálogo Propiedades de objeto OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Observaciones

Esta página muestra la ubicación del elemento vinculado y permite al usuario actualizar o interrumpir el vínculo al elemento.

Para obtener más `OLEUILINKPROPS` información sobre la estructura, consulte el Windows SDK.

## <a name="colepropertiesdialogm_op"></a><a name="m_op"></a>COlePropertiesDialog::m_op

Estructura de tipo [OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw), que se utiliza para inicializar el cuadro de diálogo Propiedades de objeto OLE comunes.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Observaciones

Esta estructura contiene miembros utilizados para inicializar el General, Vínculo, y Ver páginas.

Para obtener más información, vea las estructuras OLEUIOBJECTPROPS y [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw) en el Windows SDK.

## <a name="colepropertiesdialogm_psh"></a><a name="m_psh"></a>COlePropertiesDialog::m_psh

Estructura de tipo [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2), cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Observaciones

Después de `COlePropertiesDialog` construir un `m_psh` objeto, puede usar para establecer varios `DoModal` aspectos del cuadro de diálogo antes de llamar a la función miembro.

Si modifica `m_psh` el miembro de datos directamente, invalidará cualquier comportamiento predeterminado.

Para obtener más `PROPSHEETHEADER` información sobre la estructura, consulte el Windows SDK.

## <a name="colepropertiesdialogm_vp"></a><a name="m_vp"></a>COlePropertiesDialog::m_vp

Estructura de tipo [OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw), que se utiliza para inicializar la página Vista del cuadro de diálogo Propiedades del objeto OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Observaciones

Esta página permite al usuario alternar entre las vistas "contenido" e "icónicas" del objeto y cambiar su escala dentro del contenedor. También permite al usuario acceder al cuadro de diálogo Cambiar icono cuando el objeto se muestra como un icono.

Para obtener más `OLEUIVIEWPROPS` información sobre la estructura, consulte el Windows SDK.

## <a name="colepropertiesdialogonapplyscale"></a><a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale

Llamado por el marco de trabajo cuando el valor de escalado ha cambiado y ok o aplicar se seleccionó.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento a cuyas propiedades se tiene acceso.

*nCurrentScale*<br/>
Valor numérico de la escala del cuadro de diálogo.

*bRelativeToOrig*<br/>
Indica si la escala se aplica al tamaño original del elemento de documento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se maneja; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada. Debe invalidar esta función para habilitar los controles de escalado.

> [!NOTE]
> Antes de que se muestre el cuadro de diálogo Propiedades de objeto OLE común, el marco de trabajo llama a esta función con un NULL para *pItem* y un - 1 para *nCurrentScale*. Esto se hace para determinar si se deben habilitar los controles de escalado.

## <a name="see-also"></a>Consulte también

[EJEMPLO DE MFC CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Clase CPropertyPage](../../mfc/reference/cpropertypage-class.md)
