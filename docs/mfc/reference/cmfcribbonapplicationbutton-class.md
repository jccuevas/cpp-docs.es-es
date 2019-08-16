---
title: Clase CMFCRibbonApplicationButton
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
ms.openlocfilehash: d1dc8ef6e801623aa96cb4b47936413cd17f24f0
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821245"
---
# <a name="cmfcribbonapplicationbutton-class"></a>Clase CMFCRibbonApplicationButton

Implementa un botón especial situado en la esquina superior izquierda de la ventana de la aplicación. Cuando se hace clic, el botón abre un menú que contiene normalmente los comandos comunes del menú **Archivo** , tales como **Abrir**, **Guardar**y **Salir**.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Construye e inicializa un objeto `CMFCRibbonApplicationButton`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonApplicationButton::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Asigna una imagen al botón de la aplicación de la cinta de opciones.|

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonApplicationButton` . En el ejemplo se muestra cómo asignar una imagen al botón de la aplicación y cómo establecer su información sobre herramientas. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonBar. h

##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

Construye e inicializa un objeto [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) .

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Parámetros

*uiBmpResID*<br/>
IDENTIFICADOR de recurso de la imagen que se va a mostrar en el botón de la aplicación.

*hBmp*<br/>
Identificador de un mapa de bits que se va a mostrar en el botón de la aplicación.

### <a name="remarks"></a>Comentarios

El botón aplicación de cinta es un botón especial que se encuentra en la esquina superior izquierda de la ventana de la aplicación. Cuando un usuario hace clic en este botón, la aplicación abre un menú que normalmente contiene comandos de **archivo** comunes, como **abrir**, **Guardar**y **salir**.

##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage

Asigna una imagen al botón de la aplicación.

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Parámetros

*uiBmpResID*<br/>
de IDENTIFICADOR de recurso de la imagen que se va a mostrar en el botón de la aplicación.

*hBmp*<br/>
de Identificador de un mapa de bits que se va a mostrar en el botón de la aplicación.

### <a name="remarks"></a>Comentarios

Use este método para asignar una nueva imagen al botón aplicación de la cinta de opciones después de crear el botón. El botón aplicación se encuentra en la esquina superior izquierda de la ventana de la aplicación.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)
