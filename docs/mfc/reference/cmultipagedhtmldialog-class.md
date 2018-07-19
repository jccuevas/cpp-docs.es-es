---
title: Clase CMultiPageDHtmlDialog | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
dev_langs:
- C++
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1a4ca77e4b7a2cda10d87bd657e73931a50612
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038011"
---
# <a name="cmultipagedhtmldialog-class"></a>Clase CMultiPageDHtmlDialog
Un cuadro de diálogo de varias páginas muestra varias páginas HTML secuencialmente y administra los eventos de cada página.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Construye un objeto de cuadro de diálogo de varias páginas (similar a un asistente) DHTML.|  
|[CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|Destruye un objeto de cuadro de diálogo DHTML varias páginas.|  
  
## <a name="remarks"></a>Comentarios  
 El mecanismo para hacer esto es un [mapa de eventos DHTML y la dirección URL](dhtml-event-maps.md), que contiene incrustado mapas de eventos para cada página.  
  
## <a name="example"></a>Ejemplo  
 Este cuadro de diálogo de varias páginas supone tres recursos HTML que definen una funcionalidad similar de asistente simple. La primera página tiene un `Next` botón, el segundo un **Prev** y `Next` botón y el tercero un **Prev** botón. Cuando se presiona uno de los botones, llama a una función de controlador [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) para cargar la página nueva adecuada.  
  
 Las partes pertinentes de la declaración de clase (en CMyMultiPageDlg.h):  
  
 [!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]  
  
 Las partes pertinentes de la implementación de la clase (en CMyMultipageDlg.cpp):  
  
 [!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]  
  
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
  
##  <a name="cmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::CMultiPageDHtmlDialog  
 Construye un objeto de cuadro de diálogo de varias páginas (similar a un asistente) DHTML.  
  
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
 *lpszTemplateName*  
 La cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.  
  
 *szHtmlResID*  
 La cadena terminada en null que es el nombre de un recurso HTML.  
  
 *pParentWnd*  
 Un puntero al objeto de ventana primaria o propietaria (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, ventana primaria del objeto de cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
 *nIDTemplate*  
 Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.  
  
 *nHtmlResID*  
 Contiene el número de identificación de un recurso HTML.  
  
##  <a name="_dtorcmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog  
 Destruye un objeto de cuadro de diálogo DHTML varias páginas.  
  
```  
virtual ~CMultiPageDHtmlDialog();
```  
  
## <a name="see-also"></a>Vea también  
 [CDHtmlDialog (clase)](../../mfc/reference/cdhtmldialog-class.md)
