---
title: "Crear una aplicación de MFC estilo explorador Web | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfcweb.project
dev_langs:
- C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications, creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
caps.latest.revision: 9
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
ms.openlocfilehash: ccfb093a65c3f9a72b6180c4f415a92ebaf18684
ms.lasthandoff: 02/24/2017

---
# <a name="creating-a-web-browser-style-mfc-application"></a>Crear una aplicación MFC estilo explorador web
Una aplicación de estilo explorador Web puede tener acceso a información de Internet (como documentos activos o HTML) o una intranet, así como carpetas en el sistema de archivos local y en una red. Al derivar de la clase de vista de la aplicación de [CHtmlView](../../mfc/reference/chtmlview-class.md), eficaz que un explorador Web de la aplicación proporcionando la vista con el control WebBrowser.  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Para crear una aplicación de explorador Web basada en la arquitectura documento/vista MFC  
  
1.  Siga las instrucciones de [crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  En el Asistente para aplicaciones MFC [tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) página, compruebe que la **arquitectura documento/vista** casilla está activada. (Puede elegir **único documento** o **varios documentos**, pero no **diálogo según**.)  
  
3.  En el [revisar las clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) , utilice el **clase Base** menú desplegable para seleccionar `CHtmlView`.  
  
4.  Seleccione las opciones que desee integradas en la aplicación esqueleto.  
  
5.  Haga clic en **Finalizar**.  
  
 Este control permite la exploración del Web mediante hipervínculos y la navegación de un localizador uniforme de recursos (URL). El control mantiene una lista de historial que permite al usuario explorar hacia delante y hacia atrás en examinadas anteriormente sitios, carpetas y documentos. El control administra directamente la navegación, hipervínculos, listas de historial, favoritos y seguridad. Las aplicaciones pueden utilizar el control WebBrowser como un contenedor de documentos activos para alojar también documentos activos. Por lo tanto, puede abrir y editar en contexto desde el control WebBrowser documentos con formato enriquecido como hojas de cálculo de Microsoft Excel o Word. El control WebBrowser también es un contenedor de controles ActiveX que puede alojar cualquier control ActiveX.  
  
> [!NOTE]
>  El control WebBrowser ActiveX (y, por tanto, `CHtmlView`) sólo está disponible para aplicaciones que se ejecutan en versiones de Windows en que Internet Explorer 4.0 o posterior se haya instalado.  
  
 Porque `CHtmlView` implementa simplemente el control de explorador Web de Microsoft, su compatibilidad para la impresión no es igual que otro [CView](../../mfc/reference/cview-class.md)-las clases derivadas. En su lugar, el control WebBrowser implementa la interfaz de usuario de la impresora y la impresión. Como resultado, `CHtmlView` does admite la vista previa de impresión y el marco de trabajo no proporciona otras funciones de compatibilidad de impresión: por ejemplo, [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), y [OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), que están disponibles en otras aplicaciones MFC.  
  
 `CHtmlView`actúa como un contenedor para el control de explorador Web, que proporciona una vista Web o una página HTML de la aplicación. El asistente crea una invalidación para el [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) función en la clase de vista y proporciona un vínculo de exploración al sitio Web de Microsoft Visual C++:  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
    NULL,
    NULL);

} 
```  
  
 Puede reemplazar este sitio con uno propio, o puede usar el [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) función miembro para abrir una página HTML que resida en el script de recursos del proyecto como contenido predeterminado de la vista. Por ejemplo:  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);

} 
```  
  
## <a name="see-also"></a>Vea también  
 [Este ejemplo de MFC](http://msdn.microsoft.com/en-us/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md)   
 [Implementación de aplicaciones](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


