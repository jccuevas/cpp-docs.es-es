---
title: Clase CMultiPageDHtmlDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
dev_langs:
- C++
helpviewer_keywords:
- CMultiPageDHtmlDialog class
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c00af20731b2c47a0074366722da3f4a0711ef85
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmultipagedhtmldialog-class"></a>Clase CMultiPageDHtmlDialog
Un cuadro de diálogo de varias páginas muestra varias páginas HTML secuencialmente y administra los eventos de cada página.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Construye un objeto de cuadro de diálogo de varias páginas (estilo de asistente) DHTML.|  
|[CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|Destruye un objeto de cuadro de diálogo DHTML varias páginas.|  
  
## <a name="remarks"></a>Comentarios  
 El mecanismo para hacerlo es un [mapa de eventos DHTML y la dirección URL](http://msdn.microsoft.com/en-us/2a7332f0-79d7-46e4-b816-0a618c46777a), que contiene [incrustado mapas de eventos](http://msdn.microsoft.com/library/5346210f-f8b7-4e28-9d2c-d9d7fd42421d) para cada página.  
  
## <a name="example"></a>Ejemplo  
 Este cuadro de diálogo de varias páginas supone tres recursos HTML que definen la funcionalidad de tipo asistente sencilla. La primera página tiene un `Next` button, el segundo un **Prev** y `Next` botón y el tercero un **Prev** botón. Cuando se presiona uno de los botones, llama a una función de controlador [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) para cargar la nueva página adecuada.  
  
 Las partes pertinentes de la declaración de clase (en CMyMultiPageDlg.h):  
  
 [!code-cpp[NVC_MFCDocView&#181;](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]  
  
 Las partes pertinentes de la implementación de la clase (en CMyMultipageDlg.cpp):  
  
 [!code-cpp[NVC_MFCDocView&#182;](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdhtml.h  
  
##  <a name="cmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::CMultiPageDHtmlDialog  
 Construye un objeto de cuadro de diálogo de varias páginas (estilo de asistente) DHTML.  
  
```  
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,  
    LPCTSTR szHtmlResID = NULL,  
    CWnd* pParentWnd = NULL);

 
CMultiPageDHtmlDialog(
    UINT nIDTemplate,  
    UINT nHtmlResID = 0,  
    CWnd* pParentWnd = NULL);  
  
CMultiPageDHtmlDialog();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTemplateName`  
 Cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.  
  
 `szHtmlResID`  
 Cadena terminada en null que es el nombre de un recurso HTML.  
  
 `pParentWnd`  
 Un puntero al objeto de ventana primaria o propietaria (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es **NULL**, ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.  
  
 `nIDTemplate`  
 Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.  
  
 `nHtmlResID`  
 Contiene el número de identificación de un recurso HTML.  
  
##  <a name="_dtorcmultipagedhtmldialog"></a>CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog  
 Destruye un objeto de cuadro de diálogo DHTML varias páginas.  
  
```  
virtual ~CMultiPageDHtmlDialog();
```  
  
## <a name="see-also"></a>Vea también  
 [Clase CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

