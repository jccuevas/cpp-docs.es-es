---
title: COlePropertiesDialog (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bd1e6953d936106f272aa8bef4243728d742d8c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078198"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog (clase)

Encapsula el cuadro de diálogo Propiedades de objeto de OLE común de Windows.

## <a name="syntax"></a>Sintaxis

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Construye un objeto `COlePropertiesDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Lo llama el marco cuando el escalado del elemento de documento ha cambiado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Una estructura utilizada para inicializar la página "General" de un `COlePropertiesDialog` objeto.|
|[COlePropertiesDialog::m_lp](#m_lp)|Una estructura utilizada para inicializar la página "Link" de un `COlePropertiesDialog` objeto.|
|[COlePropertiesDialog::m_op](#m_op)|Una estructura utilizada para inicializar el `COlePropertiesDialog` objeto.|
|[COlePropertiesDialog::m_psh](#m_psh)|Una estructura que se usa para agregar páginas de propiedades personalizadas adicionales.|
|[COlePropertiesDialog::m_vp](#m_vp)|Una estructura utilizada para personalizar la página de "Vista" de un `COlePropertiesDialog` objeto.|

## <a name="remarks"></a>Comentarios

Cuadros de diálogo comunes de propiedades del objeto OLE proporcionan una manera fácil para mostrar y modificar las propiedades de un elemento de documento OLE de manera coherente con los estándares de Windows. Estas propiedades incluyen, entre otros, información sobre el archivo representado por el elemento del documento, las opciones para mostrar el icono y la escala de la imagen y la información en el vínculo del elemento (si el elemento está vinculado).

Para usar un `COlePropertiesDialog` , primero cree el objeto con el `COlePropertiesDialog` constructor. Una vez que se ha construido el cuadro de diálogo, llame a la `DoModal` la función miembro para mostrar el cuadro de diálogo y permitir que el usuario modificar las propiedades del elemento. `DoModal` Devuelve si el usuario seleccionó Aceptar (IDOK) o en el botón Cancelar (IDCANCEL). Además de los botones Aceptar y Cancelar, hay un botón Aplicar. Cuando el usuario selecciona aplicar, los cambios realizados en las propiedades del elemento de documento se aplican al elemento y su imagen se actualiza automáticamente, pero sigue estando activa.

El [m_psh](#m_psh) miembro de datos es un puntero a un `PROPSHEETHEADER` estructura y en la mayoría de los casos no necesitará tener acceso a ella explícitamente. Una excepción es cuando necesite páginas de propiedades adicionales más allá de las páginas de General, ver y vincular de forma predeterminada. En este caso, puede modificar el `m_psh` miembro de datos para incluir las páginas personalizadas antes de llamar a la `DoModal` función miembro.

Para obtener más información sobre los cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).

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
Puntero al elemento de documento cuyas propiedades se tiene acceso.

*nScaleMin*<br/>
Porcentaje mínimo de escala de la imagen de elemento de documento.

*nScaleMax*<br/>
Máximo porcentaje de la imagen de elemento de documento de escala.

*pParentWnd*<br/>
Puntero en el cuadro de diálogo principal o propietaria.

### <a name="remarks"></a>Comentarios

Derive la clase de cuadro de diálogo Propiedades del objeto OLE común de `COlePropertiesDialog` con el fin de implementar el escalado para los elementos del documento. Los cuadros de diálogo que se implementa mediante una instancia de esta clase no será compatible con la escala del elemento de documento.

De forma predeterminada, el cuadro de diálogo Propiedades del objeto OLE común tiene tres páginas de forma predeterminada:

- General

   Esta página contiene información del sistema para el archivo representado por el elemento del documento seleccionado. Desde esta página, el usuario puede convertir el elemento seleccionado en otro tipo.

- Ver

   Esta página contiene las opciones para mostrar el elemento, cambiar el icono y cambiar la escala de la imagen.

- Vínculo

   Esta página contiene opciones para cambiar la ubicación del elemento vinculado y actualizar el elemento vinculado. Desde esta página, el usuario puede romper el vínculo del elemento seleccionado.

Para agregar páginas más allá de los proporcionados de forma predeterminada, modifique la [m_psh](#m_psh) variable miembro antes de salir el constructor de su `COlePropertiesDialog`-clase derivada. Se trata de una implementación avanzada de la `COlePropertiesDialog` constructor.

##  <a name="domodal"></a>  COlePropertiesDialog::DoModal

Llame a esta función miembro para mostrar el cuadro de diálogo de propiedades del objeto OLE común de Windows y permitir que el usuario ver o cambiar las distintas propiedades del elemento de documento.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL si se realiza correctamente; en caso contrario, es 0. IDOK e IDCANCEL son las constantes que indican si el usuario seleccionó el botón Aceptar o Cancelar.

Si se devuelve IDCANCEL, puede llamar a la Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) función para determinar si se produjo un error.

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

Una estructura de tipo [OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa), que se usa para inicializar la página General del cuadro de diálogo Propiedades del objeto OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Comentarios

Esta página muestra el tipo y tamaño de una inclusión y permite al usuario acceso al cuadro de diálogo convertir. Esta página también muestra el destino del vínculo si el objeto es un vínculo.

Para obtener más información sobre la `OLEUIGNRLPROPS` estructura, vea el SDK de Windows.

##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp

Una estructura de tipo [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa), que se usa para inicializar la página de vínculo del cuadro de diálogo Propiedades del objeto OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Comentarios

Esta página muestra la ubicación del elemento vinculado y permite al usuario actualizar o interrumpir el vínculo al elemento.

Para obtener más información sobre la `OLEUILINKPROPS` estructura, vea el SDK de Windows.

##  <a name="m_op"></a>  COlePropertiesDialog::m_op

Una estructura de tipo [OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa), que se usa para inicializar el cuadro de diálogo Propiedades del objeto OLE común.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Comentarios

Esta estructura contiene a miembros que se utilizan para inicializar las páginas General, el vínculo y la vista.

Para obtener más información, consulte el OLEUIOBJECTPROPS y [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa) estructuras en el SDK de Windows.

##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh

Una estructura de tipo [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2), cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Comentarios

Después de crear un `COlePropertiesDialog` objeto, puede usar `m_psh` para establecer varios aspectos del cuadro de diálogo antes de llamar a la `DoModal` función miembro.

Si modifica el `m_psh` miembro de datos directamente, invalidará cualquier comportamiento predeterminado.

Para obtener más información sobre la `PROPSHEETHEADER` estructura, vea el SDK de Windows.

##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp

Una estructura de tipo [OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa), que se usa para inicializar la página de vista del cuadro de diálogo Propiedades del objeto OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Comentarios

Esta página permite al usuario alternar entre "content" y "icónico" vistas del objeto y cambiar su valor de scaling dentro del contenedor. También permite al usuario acceso al cuadro de diálogo Cambiar icono cuando el objeto se muestra como un icono.

Para obtener más información sobre la `OLEUIVIEWPROPS` estructura, vea el SDK de Windows.

##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale

Lo llama el marco de trabajo cuando ha cambiado el valor de escala y se seleccionó Aceptar o aplicar.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento de documento cuyas propiedades se tiene acceso.

*nCurrentScale*<br/>
Valor numérico de la escala del cuadro de diálogo.

*bRelativeToOrig*<br/>
Indica si el escalado se aplica al tamaño original del elemento de documento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controló; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada no hace nada. Se debe reemplazar esta función para habilitar los controles de escala.

> [!NOTE]
>  Antes de mostrar el cuadro de diálogo Propiedades del objeto OLE común, el marco llama a esta función con un valor NULL para *pItem* y a - 1 para *nCurrentScale*. Esto se hace para determinar si los controles de escala deben estar habilitados.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CIRC](../../visual-cpp-samples.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage (clase)](../../mfc/reference/cpropertypage-class.md)
