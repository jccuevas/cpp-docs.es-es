---
title: Clase CMFCRibbonSeparator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSeparator class
- GetThisClass method
- CreateObject method
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 98a58d43b5e6299f26521d873caec06d4581f7b3
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonseparator-class"></a>Clase CMFCRibbonSeparator
Implementa el separador de la cinta de opciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonSeparator : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Construye un objeto `CMFCRibbonSeparator`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Agrega un separador a la **comandos** lista en la **personalizar** cuadro de diálogo. (Invalida [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|  
|`CMFCRibbonSeparator::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonSeparator::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Un método de copia que establece las variables de miembro de un separador de otro objeto.|  
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Devuelve el tamaño de un separador.|  
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Indica si se trata de un separador.|  
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Indica si se trata de una tabulación.|  
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Llamado por el sistema para dibujar el separador en la cinta de opciones o la barra de herramientas de acceso rápido.|  
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Llamado por el sistema para dibujar el separador en la **comandos** lista.|  
  
## <a name="remarks"></a>Comentarios  
 Un separador de cinta es una línea vertical u horizontal que lógicamente separa la cinta de opciones elementos. Puede extraer un separador en el control de la cinta de opciones, el menú principal de la aplicación, la barra de estado de la cinta de opciones y la barra de herramientas de acceso rápido.  
  
 Para utilizar un separador en la aplicación, construya el objeto nuevo y agregarlo al menú principal de la aplicación, como se muestra aquí:  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```  
Llame a [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) agregar separadores a paneles de cinta. Los separadores se asignan y se agregó internamente por el `AddSeparator` (método).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxbaseribbonelement.h  
  
##  <a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox  
 Agrega un separador a la **comandos** lista en la **personalizar** cuadro de diálogo.  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndListBox`  
 Un puntero a la **comandos** donde se agrega el separador de lista.  
  
 [in] `bDeep`  
 ignorado.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero en la cadena en el cuadro de lista especificado por `pWndListBox`.  
  
##  <a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator  
 Construye un objeto `CMFCRibbonSeparator`.  
  
```  
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsHoriz`  
 Si `TRUE`, el separador es horizontal; si `FALSE`, el separador es vertical.  
  
### <a name="remarks"></a>Comentarios  
 Separadores horizontales se utilizan en los menús de la aplicación. En las barras de herramientas se utilizan separadores verticales.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonSeparator` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp Nº&19;](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCRibbonSeparator::CopyFrom  
 Un método de copia que establece las variables de miembro de un separador de otro objeto.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `Src`  
 Elemento de la cinta de origen que lo copien.  
  
##  <a name="getregularsize"></a>CMFCRibbonSeparator::GetRegularSize  
 Devuelve el tamaño de un separador.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero a un contenido de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del separador en el contexto de dispositivo especificado.  
  
##  <a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator  
 Indica si se trata de un separador.  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre `TRUE` para esta clase.  
  
##  <a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop  
 Indica si se trata de una tabulación.  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre `FALSE` para esta clase.  
  
### <a name="remarks"></a>Comentarios  
 Un separador de la cinta de opciones no es una tabulación.  
  
##  <a name="ondraw"></a>CMFCRibbonSeparator::OnDraw  
 Llamado por el sistema para dibujar el separador en la cinta de opciones o la barra de herramientas de acceso rápido.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
##  <a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList  
 Llamado por el sistema para dibujar el separador en la **comandos** lista.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pDC`|Puntero a un contexto de dispositivo.|  
|[in] `strText`|Texto que aparece en la lista.|  
|[in] `nTextOffset`|Espaciado entre el texto y el lado izquierdo del rectángulo delimitador.|  
|[in] `rect`|Especifica el rectángulo delimitador.|  
|[in] `bIsSelected`|ignorado.|  
|[in] `bHighlighted`|ignorado.|  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

