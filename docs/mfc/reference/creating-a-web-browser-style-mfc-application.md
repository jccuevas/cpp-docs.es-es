---
title: Crear una aplicación de MFC estilo explorador Web | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcweb.project
dev_langs:
- C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3b0e148104ff5620eddf7ac0d26693d96607d9
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39025661"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Crear una aplicación MFC estilo explorador web
Una aplicación de estilo explorador Web puede tener acceso a información desde Internet (por ejemplo, HTML o documentos activos) o una intranet, así como las carpetas del sistema de archivos local y en una red. Al derivar la clase de vista de la aplicación de [CHtmlView](../../mfc/reference/chtmlview-class.md), eficaz que un explorador Web de la aplicación, ya que proporciona la vista con el control WebBrowser.  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Para crear una aplicación de explorador Web basada en la arquitectura documento/vista MFC  
  
1.  Siga las instrucciones de [crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  En el Asistente para aplicaciones MFC [tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) página, compruebe que la **arquitectura documento/vista** está activada. (Puede elegir **único documento** o **varios documentos**, pero no **en función del cuadro de diálogo**.)  
  
3.  En el [revisar las clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) , utilice el **clase Base** menú desplegable para seleccionar `CHtmlView`.  
  
4.  Seleccione las opciones que desee integradas en la aplicación esquema.  
  
5.  Haga clic en **Finalizar**.  
  
 El control WebBrowser admite la exploración Web a través de los hipervínculos y navegación de localizador uniforme de recursos (URL). El control mantiene una lista de historial que permite al usuario examinar hacia delante y hacia atrás en anteriormente para examinar documentos, carpetas y sitios. El control administra directamente la navegación, hipervínculos, las listas del historial, favoritos y seguridad. Las aplicaciones pueden usar el control WebBrowser como un contenedor de documentos activos a documentos de activos de host. Por lo tanto, puede abrir y editar en contexto desde el control WebBrowser documentos con formato enriquecido como hojas de cálculo de Microsoft Excel o Word. El control WebBrowser también es un contenedor de controles ActiveX que puede alojar cualquier control ActiveX.  
  
> [!NOTE]
>  El control WebBrowser ActiveX (y, por tanto, `CHtmlView`) solo está disponible para aplicaciones que se ejecutan en versiones de Windows en Internet Explorer 4.0 o posterior instalado.  
  
 Dado que `CHtmlView` implementa simplemente el control del explorador Web de Microsoft, su compatibilidad para la impresión no es igual que otro [CView](../../mfc/reference/cview-class.md)-las clases derivadas. En su lugar, el control WebBrowser implementa la interfaz de usuario de la impresora y la impresión. Como resultado, `CHtmlView` does no se admite la vista previa de impresión y el marco de trabajo no proporciona otras funciones de compatibilidad de impresión: por ejemplo, [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), y [OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), que están disponibles en otras aplicaciones MFC.  
  
 `CHtmlView` actúa como un contenedor para el control del explorador Web, que proporciona una vista Web o una página HTML de la aplicación. El asistente crea una invalidación para el [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) función en la clase de vista, que proporciona un vínculo de exploración al sitio Web de Microsoft Visual C++:  
  
```cpp
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
        NULL,
        NULL);
}
```

Puede reemplazar este sitio con uno propio, o puede usar el [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) función miembro para abrir una página HTML que reside en el script de recursos del proyecto como el contenido predeterminado para la vista. Por ejemplo:  
  
```cpp
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);
}
```  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFCIE de MFC](http://msdn.microsoft.com/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Trabajar con las propiedades del proyecto](../../ide/working-with-project-properties.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Trabajar con las propiedades del proyecto](../../ide/working-with-project-properties.md)   
 [Implementación de aplicaciones](http://msdn.microsoft.com/4ff8881d-0daf-47e7-bfe7-774c625031b4)

