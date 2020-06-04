---
title: Crear una aplicación MFC estilo explorador web
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: e02e928f65ab4cd918e730135abc62ed3237decf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215129"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Crear una aplicación MFC estilo explorador web

Una aplicación de estilo de explorador Web puede tener acceso a información de Internet (por ejemplo, documentos HTML o activos) o una intranet, así como carpetas del sistema de archivos local y de una red. Al derivar la clase de vista de la aplicación de [CHtmlView](../../mfc/reference/chtmlview-class.md), se hace que la aplicación sea un explorador Web proporcionando la vista con el control WebBrowser.

## <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Para crear una aplicación de explorador Web basada en la arquitectura documento/vista de MFC

1. Siga las instrucciones de [creación de una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md).

1. En la página tipo de [aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC, asegúrese de que está seleccionado el cuadro **arquitectura de documento/vista** . (Puede elegir **uno o** **varios documentos**, pero no **basados en cuadros de diálogo**).

1. En la página [revisar clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) , use el menú desplegable **clase Base** para seleccionar `CHtmlView`.

1. Seleccione cualquier otra opción que desee integrar en la aplicación esqueleto.

1. Haga clic en **Finalizar**

El control WebBrowser admite la exploración Web a través de hipervínculos y la navegación de localizador uniforme de recursos (URL). El control mantiene una lista de historial que permite al usuario explorar hacia delante y hacia atrás a través de sitios, carpetas y documentos examinados previamente. El control controla directamente la navegación, los hipervínculos, las listas de historial, los favoritos y la seguridad. Las aplicaciones pueden usar el control WebBrowser como un contenedor de documentos activo para hospedar documentos activos también. Por lo tanto, los documentos con formato enriquecido, como hojas de cálculo de Microsoft Excel o documentos de Word, se pueden abrir y editar en contexto desde el control WebBrowser. El control WebBrowser es también un contenedor de controles ActiveX que puede hospedar cualquier control ActiveX.

> [!NOTE]
> El control ActiveX WebBrowser (y por tanto `CHtmlView`) solo está disponible para las aplicaciones que se ejecutan en versiones de Windows en las que se ha instalado Internet Explorer 4,0 o posterior.

Dado que `CHtmlView` simplemente implementa el control de explorador Web de Microsoft, su compatibilidad con la impresión no es como otras clases derivadas de [CView](../../mfc/reference/cview-class.md). En su lugar, el control WebBrowser implementa la interfaz de usuario de la impresora y la impresión. Como resultado, `CHtmlView` no admite la vista previa de impresión y el marco no proporciona otras funciones de soporte de impresión: por ejemplo, [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)y [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onendprinting), que están disponibles en otras aplicaciones MFC.

`CHtmlView` actúa como contenedor para el control de explorador Web, que ofrece a la aplicación una vista en una página web o HTML. El asistente crea una invalidación para la función [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) en la clase de vista, y proporciona un vínculo de navegación al C++ sitio web de Microsoft Visual:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

Puede reemplazar este sitio por uno propio, o puede usar la función miembro [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) para abrir una página HTML que resida en el script de recursos del proyecto como contenido predeterminado de la vista. Por ejemplo:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>Consulte también

[Ejemplo MFCIE de MFC](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet)<br/>
[Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Set compiler and build properties](../../build/working-with-project-properties.md) (Establecer las propiedades del compilador y la compilación)<br/>
[Páginas de propiedades](../../build/reference/property-pages-visual-cpp.md)<br/>
[Set compiler and build properties](../../build/working-with-project-properties.md) (Establecer las propiedades del compilador y la compilación)
