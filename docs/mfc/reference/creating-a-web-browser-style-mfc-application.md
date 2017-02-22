---
title: "Crear una aplicaci&#243;n MFC estilo Explorador Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcweb.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC, aplicaciones web"
  - "aplicaciones web, crear"
  - "exploradores Web"
  - "exploradores Web, crear a partir de la arquitectura MFC"
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Crear una aplicaci&#243;n MFC estilo Explorador Web
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una aplicación estilo explorador web puede tener acceso a información de Internet \(como documentos activos o HTML\) o de una intranet, así como a carpetas del sistema local de archivos o de la red.  Si deriva la clase de la vista de la aplicación de [CHtmlView](../../mfc/reference/chtmlview-class.md), convierte la aplicación en un explorador web al proporcionar a la vista el control WebBrowser.  
  
### Para crear una aplicación de explorador web basada en la arquitectura documento\/vista de MFC  
  
1.  Siga las instrucciones descritas en [Crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  En la página [Tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC, asegúrese de que la casilla **Compatibilidad con la arquitectura documento\/vista** está activada. Puede elegir **Documento único** o **Múltiples documentos**, pero no **Basada en cuadros de diálogo**.  
  
3.  En la página [Clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md), utilice el menú desplegable **Clase base** para seleccionar `CHtmlView`.  
  
4.  Seleccione las opciones que desee incorporar a la aplicación esqueleto.  
  
5.  Haga clic en **Finalizar**.  
  
 Este control permite la exploración del Web mediante hipervínculos y la navegación en direcciones URL \(Localizador de recursos universal\).  El control mantiene una lista de historial que permite al usuario explorar hacia atrás y hacia delante los sitios, carpetas y documentos explorados previamente.  Este control administra directamente la navegación, los hipervínculos, las listas de historial, la lista de favoritos y la seguridad.  Las aplicaciones pueden utilizar también el control WebBrowser como un contenedor de documentos activos para hospedar también documentos activos.  Por tanto, los documentos con formato complejo, como las hojas de cálculo de Microsoft Excel o los documentos de Word, pueden abrirse y editarse en el contexto desde el control WebBrowser.  Este control también es un contenedor de controles ActiveX que puede hospedar cualquier control ActiveX.  
  
> [!NOTE]
>  El control ActiveX WebBrowser \(y, por tanto, `CHtmlView`\) sólo está disponible para aplicaciones que se ejecutan en versiones de Windows en las que esté instalado Internet Explorer 4.0 o posterior.  
  
 Como `CHtmlView` implementa simplemente el control explorador web de Microsoft, su compatibilidad para la impresión no es como en las otras clases derivadas de [CView](../../mfc/reference/cview-class.md).  En lugar de ello, el control WebBrowser implementa la interfaz de usuario de impresora y la impresión en sí.  En consecuencia, `CHtmlView` no admite la vista previa de impresión y el marco de trabajo no proporciona otras funciones de compatibilidad para la impresión: por ejemplo, [CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md), [CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md) y [CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md), que sí están disponibles en otras aplicaciones MFC.  
  
 `CHtmlView` actúa como un contenedor del control explorador web, que proporciona a la aplicación una vista de sitios Web o páginas HTML.  El asistente crea una función que reemplaza la función [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) de la clase de vista y proporciona un vínculo de navegación al sitio Web de Microsoft Visual C\+\+:  
  
```  
void CWebView::OnInitialUpdate()  
{  
   CHtmlView::OnInitialUpdate();  
  
   // TODO: This code navigates to a popular spot on the web.  
   //  change the code to go where you'd like.  
   Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),NULL,NULL);  
}  
```  
  
 Puede reemplazar este sitio con uno propio, o utilizar la función miembro [LoadFromResource](../Topic/CHtmlView::LoadFromResource.md) para abrir una página HTML que resida en el script de recursos del proyecto como contenido predeterminado de la vista.  Por ejemplo:  
  
```  
void CWebView::OnInitialUpdate()  
{  
   CHtmlView::OnInitialUpdate();  
  
   // TODO: This code navigates to a popular spot on the web.  
   //  change the code to go where you'd like.  
   LoadFromResource(IDR_HTML1);  
}  
```  
  
## Vea también  
 [MFC Sample MFCIE](http://msdn.microsoft.com/es-es/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md)   
 [Deploying Applications](http://msdn.microsoft.com/es-es/4ff8881d-0daf-47e7-bfe7-774c625031b4)