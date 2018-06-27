---
title: Clase CDragListBox | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
dev_langs:
- C++
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78f2c1843602c1c1db6b05a16bbea0aceec70df2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955994"
---
# <a name="cdraglistbox-class"></a>Clase CDragListBox
Además de proporcionar la funcionalidad de un cuadro de lista de Windows, la `CDragListBox` clase permite al usuario mover elementos de cuadro de lista, como los nombres de archivo, en el cuadro de lista.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDragListBox : public CListBox  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](#cdraglistbox)|Construye un objeto `CDragListBox`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](#begindrag)|Llamado por el marco de trabajo cuando se inicia una operación de arrastre.|  
|[CDragListBox::CancelDrag](#canceldrag)|Llamado por el marco de trabajo cuando se ha cancelado una operación de arrastre.|  
|[CDragListBox::Dragging](#dragging)|Lo llama el marco de trabajo durante una operación de arrastre.|  
|[CDragListBox::DrawInsert](#drawinsert)|Dibuja a la Guía de inserción del cuadro de lista de arrastre.|  
|[CDragListBox::Dropped](#dropped)|Llamado por el marco de trabajo cuando se ha eliminado el elemento.|  
|[CDragListBox::ItemFromPt](#itemfrompt)|Devuelve las coordenadas del elemento que se están arrastrando.|  
  
## <a name="remarks"></a>Comentarios  
 Cuadros de lista con esta capacidad de permiten a los usuarios ordenar los elementos en una lista de la manera más útil para ellos. De forma predeterminada, el cuadro de lista moverá el elemento a la nueva ubicación en la lista. Sin embargo, `CDragListBox` objetos se pueden personalizar para copiar elementos en lugar de moverlos.  
  
 El control de cuadro de lista asociado a la `CDragListBox` clase no debe tener la **LBS_SORT** o **LBS_MULTIPLESELECT** estilo. Para obtener una descripción de los estilos de cuadro de lista, vea [estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).  
  
 Para usar un cuadro de lista de arrastre en un cuadro de diálogo existente de la aplicación, agregue un control de cuadro de lista a la plantilla de cuadro de diálogo con el editor de cuadro de diálogo y, a continuación, asignar una variable miembro (de categoría `Control` y el tipo de Variable `CDragListBox`) correspondiente al cuadro de lista control de la plantilla de cuadro de diálogo.  
  
 Para obtener más información sobre la asignación de controles a las variables de miembro, vea [acceso directo para definir Variables miembro para los controles de cuadro de diálogo](../../windows/defining-member-variables-for-dialog-controls.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="begindrag"></a>  CDragListBox::BeginDrag  
 Llamado por el marco de trabajo cuando produce un evento que pudiera iniciar una operación de arrastre, por ejemplo, al presionar el botón primario del mouse.  
  
```  
virtual BOOL BeginDrag(CPoint pt);
```  
  
### <a name="parameters"></a>Parámetros  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas del elemento que se están arrastrando.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la arrastra puede, 0 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea controlar lo que ocurre cuando se inicia una operación de arrastre. La implementación predeterminada captura el mouse y permanece en modo de arrastre hasta que el usuario hace clic en el botón izquierdo o derecho del mouse o presione la tecla ESC, momento en el que se cancela la operación de arrastre.  
  
##  <a name="canceldrag"></a>  CDragListBox::CancelDrag  
 Llamado por el marco de trabajo cuando se ha cancelado una operación de arrastre.  
  
```  
virtual void CancelDrag(CPoint pt);
```  
  
### <a name="parameters"></a>Parámetros  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas del elemento que se están arrastrando.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para controlar cualquier procesamiento especial para el control de cuadro de lista.  
  
##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox  
 Construye un objeto `CDragListBox`.  
  
```  
CDragListBox();
```  
  
##  <a name="dragging"></a>  CDragListBox::Dragging  
 Lo llama el marco de trabajo cuando se arrastra un elemento de cuadro de lista dentro de la `CDragListBox` objeto.  
  
```  
virtual UINT Dragging(CPoint pt);
```  
  
### <a name="parameters"></a>Parámetros  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene x e y coordenadas del cursor de la pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de recurso del cursor que se mostrará. Los valores posibles son:  
  
- `DL_COPYCURSOR` Indica que se copiará el elemento.  
  
- `DL_MOVECURSOR` Indica que se moverá el elemento.  
  
- `DL_STOPCURSOR` Indica que el destino de eliminación actual no es aceptable.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado devuelve `DL_MOVECURSOR`. Reemplace esta función si desea proporcionar funcionalidad adicional.  
  
##  <a name="drawinsert"></a>  CDragListBox::DrawInsert  
 Lo llama el marco de trabajo para dibujar a la Guía de inserción antes del elemento con el índice indicado.  
  
```  
virtual void DrawInsert(int nItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *nItem*  
 Índice de base cero del punto de inserción.  
  
### <a name="remarks"></a>Comentarios  
 Un valor de - 1 borra a la Guía de inserción. Reemplace esta función para modificar la apariencia o comportamiento de la Guía de inserción.  
  
##  <a name="dropped"></a>  CDragListBox::Dropped  
 Lo llama el marco cuando un elemento se coloca dentro de un `CDragListBox` objeto.  
  
```  
virtual void Dropped(
    int nSrcIndex,  
    CPoint pt);
```  
  
### <a name="parameters"></a>Parámetros  
 *nSrcIndex*  
 Especifica el índice de base cero de la cadena colocarlo.  
  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas del sitio de destino.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado copia el elemento de cuadro de lista y sus datos a la nueva ubicación y, a continuación, elimina el elemento original. Reemplace esta función para personalizar el comportamiento predeterminado, como la habilitación de copias de los elementos de cuadro de lista que se arrastrarán a otras ubicaciones dentro de la lista.  
  
##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt  
 Llamada a esta función para recuperar el índice de base cero del elemento de cuadro de lista que se encuentra en *pt*.  
  
```  
int ItemFromPt(
    CPoint pt,  
    BOOL bAutoScroll = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas de un punto en el cuadro de lista.  
  
 *bAutoScroll*  
 Es distinto de cero si se permite el desplazamiento, 0 en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento de cuadro de lista de arrastre.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC TSTCON](../../visual-cpp-samples.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)
