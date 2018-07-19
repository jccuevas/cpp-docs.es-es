---
title: CMFCRibbonApplicationButton (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eddce134c3cda27e57a6a20d709bc4eab08d6e80
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849020"
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
|`CMFCRibbonApplicationButton::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonApplicationButton::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Asigna una imagen en el botón de la aplicación de cinta de opciones.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar distintos métodos en el `CMFCRibbonApplicationButton` clase. El ejemplo muestra cómo asignar una imagen para el botón de la aplicación y cómo establecer la información sobre herramientas. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../visual-cpp-samples.md).  
  
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
 *uiBmpResID*  
 El identificador de recurso de la imagen para mostrar en el botón de la aplicación.  
  
 *hBmp*  
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
 [in] *uiBmpResID*  
 El identificador de recurso de la imagen para mostrar en el botón de la aplicación.  
  
 [in] *hBmp*  
 Identificador de un mapa de bits que se muestra en el botón de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para asignar una nueva imagen en el botón de la aplicación de cinta después de crear el botón. El botón de la aplicación se encuentra en la esquina superior izquierda de la ventana de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)
