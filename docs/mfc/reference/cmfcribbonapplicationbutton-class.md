---
title: CMFCRibbonApplicationButton (clase)
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
ms.openlocfilehash: 892e9e56b6df5bc0a3dc0aa9cf3786e36b5311c7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302642"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton (clase)

Implementa un botón especial situado en la esquina superior izquierda de la ventana de la aplicación. Cuando se hace clic, el botón abre un menú que contiene normalmente los comandos comunes del menú **Archivo** , tales como **Abrir**, **Guardar**y **Salir**.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Construye e inicializa un objeto `CMFCRibbonApplicationButton`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonApplicationButton::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Asigna una imagen en el botón de la aplicación de cinta de opciones.|

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonApplicationButton` . El ejemplo muestra cómo asignar una imagen para el botón de la aplicación y cómo establecer la información sobre herramientas. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonBar.h

##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

Crea e inicializa un [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) objeto.

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Parámetros

*uiBmpResID*<br/>
El identificador de recurso de la imagen para mostrar en el botón de la aplicación.

*hBmp*<br/>
Identificador de un mapa de bits que se muestra en el botón de la aplicación.

### <a name="remarks"></a>Comentarios

Botón de la aplicación de cinta es un botón especial que se encuentra en la esquina superior izquierda de la ventana de la aplicación. Cuando un usuario hace clic en este botón, la aplicación abre un menú que contiene normalmente comunes **archivo** comandos, como **abierto**, **guardar**, y **Exit**.

##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage

Asigna una imagen en el botón de la aplicación.

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Parámetros

*uiBmpResID*<br/>
[in] El identificador de recurso de la imagen para mostrar en el botón de la aplicación.

*hBmp*<br/>
[in] Identificador de un mapa de bits que se muestra en el botón de la aplicación.

### <a name="remarks"></a>Comentarios

Utilice este método para asignar una nueva imagen en el botón de la aplicación de cinta después de crear el botón. El botón de la aplicación se encuentra en la esquina superior izquierda de la ventana de la aplicación.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)
