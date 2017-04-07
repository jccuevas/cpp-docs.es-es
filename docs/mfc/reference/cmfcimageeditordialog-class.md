---
title: Clase CMFCImageEditorDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorDialog class
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1a629f9699aa2d6fb185737b51b36259ce574fe0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcimageeditordialog-class"></a>Clase CMFCImageEditorDialog
La `CMFCImageEditorDialog` clase es compatible con un cuadro de diálogo del editor de imágenes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCImageEditorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Construye un objeto `CMFCImageEditorDialog`.|  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCImageEditorDialog` clase proporciona un cuadro de diálogo que incluye:  
  
-   Un área de imagen que se utiliza para modificar los píxeles individuales de una imagen.  
  
-   Herramientas para modificar los píxeles en el área de dibujo.  
  
-   Paleta de colores para especificar el color utilizado por las herramientas de dibujo.  
  
-   Área de vista previa que muestra el efecto de la edición.  
  
 En la siguiente ilustración muestra a un editor de imágenes en el cuadro de diálogo.  
  
 ![Cuadro de diálogo CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "imageedit")  
  
 Una manera de usar un `CMFCImageEditorDialog` objeto es pasarlo un `CBitmap` la imagen que desea editar. No cree una imagen grande porque el área de edición de imágenes tiene un tamaño limitado y el tamaño de píxel lógico se ajusta para adaptarse al área. Llame a la `DoModal` método para iniciar el cuadro de diálogo modal.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afximageeditordialog.h  
  
##  <a name="cmfcimageeditordialog"></a>CMFCImageEditorDialog::CMFCImageEditorDialog  
 Construye un objeto `CMFCImageEditorDialog`.  
  
```  
CMFCImageEditorDialog(
    CBitmap* pBitmap,  
    CWnd* pParent=NULL,  
    int nBitsPixel=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBitmap`  
 Puntero a una imagen.  
  
 `pParent`  
 Puntero a la ventana primaria del cuadro de diálogo de editor de imagen actual.  
  
 `nBitsPixel`  
 El número de bits utilizado para representar el color de un solo píxel, que también se conoce como profundidad de color.  Si el `nBitsPixel` parámetro es -1, la profundidad de color se deriva de la imagen especificada por el `pBitmap` parámetro. El valor predeterminado es -1.  
  
### <a name="return-value"></a>Valor devuelto  
 Para modificar una imagen, pase un puntero de la imagen a la `CMFCImageEditorDialog` constructor. A continuación, llame el `DoModal` método para abrir el cuadro de diálogo modal. Cuando el `DoModal` método vuelve, contiene la nueva imagen.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCImageEditorDialog` clase. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls Nº&8;](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]  
[!code-cpp[NVC_MFC_NewControls Nº&40;](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

