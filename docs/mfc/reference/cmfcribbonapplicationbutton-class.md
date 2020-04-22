---
title: CMFCRibbonApplicationButton (Clase)
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
ms.openlocfilehash: b28d075c5fcc4313e1a62ae731b3fad8ef4d8a12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749930"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton (Clase)

Implementa un botón especial situado en la esquina superior izquierda de la ventana de la aplicación. Cuando se hace clic, el botón abre un menú que contiene normalmente los comandos comunes del menú **Archivo** , tales como **Abrir**, **Guardar**y **Salir**.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Construye e inicializa un objeto `CMFCRibbonApplicationButton`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonApplicationButton::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Asigna una imagen al botón de aplicación de la cinta de opciones.|

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

**Encabezado:** afxRibbonBar.h

## <a name="cmfcribbonapplicationbuttoncmfcribbonapplicationbutton"></a><a name="cmfcribbonapplicationbutton"></a>CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

Construye e inicializa un [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) objeto.

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Parámetros

*uiBmpResID*<br/>
El identificador de recurso de la imagen que se va a mostrar en el botón de la aplicación.

*hBmp*<br/>
Identificador de un mapa de bits para mostrar en el botón de la aplicación.

### <a name="remarks"></a>Observaciones

El botón de aplicación de la cinta de opciones es un botón especial que se encuentra en la esquina superior izquierda de la ventana de la aplicación. Cuando un usuario hace clic en este botón, la aplicación abre un menú que normalmente contiene comandos **de archivo** comunes, como **Abrir**, **Guardar**y **Salir**.

## <a name="cmfcribbonapplicationbuttonsetimage"></a><a name="setimage"></a>CMFCRibbonApplicationButton::SetImage

Asigna una imagen al botón de la aplicación.

```cpp
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Parámetros

*uiBmpResID*<br/>
[en] El identificador de recurso de la imagen que se va a mostrar en el botón de la aplicación.

*hBmp*<br/>
[en] Identificador de un mapa de bits para mostrar en el botón de la aplicación.

### <a name="remarks"></a>Observaciones

Utilice este método para asignar una nueva imagen al botón de aplicación de la cinta de opciones después de crear el botón. El botón de aplicación se encuentra en la esquina superior izquierda de la ventana de la aplicación.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)
