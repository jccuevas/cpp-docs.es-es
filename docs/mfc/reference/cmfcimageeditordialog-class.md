---
title: Clase CMFCImageEditorDialog | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 795e5548e93323af389c3faeaefa7dda0bf7d80c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcimageeditordialog-class"></a>Clase CMFCImageEditorDialog
La `CMFCImageEditorDialog` clase es compatible con un cuadro de diálogo del editor de imágenes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCImageEditorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Construye un objeto `CMFCImageEditorDialog`.|  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCImageEditorDialog` clase proporciona un cuadro de diálogo que incluye:  
  
-   Un área de imagen que se utiliza para modificar los píxeles individuales en una imagen.  
  
-   Herramientas para modificar los píxeles en el área de dibujo.  
  
-   Una paleta de colores para especificar el color que se utiliza con las herramientas de dibujo.  
  
-   Área de vista previa que muestra el efecto de la edición.  
  
 En la siguiente ilustración muestra a un editor de imágenes de cuadro de diálogo.  
  
 ![Cuadro de diálogo CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "imageedit")  
  
 Una manera de usar un `CMFCImageEditorDialog` objeto es pasarlo un `CBitmap` imagen que se pueda editar. No cree una imagen grande porque el área de edición de imágenes tienen un tamaño limitado y el tamaño lógico del píxel se ajusta para adaptarse al área. Llame a la `DoModal` método para iniciar el cuadro de diálogo modal.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afximageeditordialog.h  
  
##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog  
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
 El número de bits que se usa para representar el color de un solo píxel, que también se denomina profundidad de color.  Si el `nBitsPixel` parámetro es -1, la intensidad de color se deriva de la imagen especificada por el `pBitmap` parámetro. El valor predeterminado es -1.  
  
### <a name="return-value"></a>Valor devuelto  
 Para modificar una imagen, pasar un puntero de imagen a la `CMFCImageEditorDialog` constructor. A continuación, llame a la `DoModal` método para abrir un cuadro de diálogo modal. Cuando el `DoModal` método devuelve el mapa de bits contiene la nueva imagen.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCImageEditorDialog` clase. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]  
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)
