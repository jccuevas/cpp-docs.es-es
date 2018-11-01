---
title: ASP, Asistente para componentes de páginas Active Server ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.asp
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
ms.openlocfilehash: c6ab66fc606b58e87ac65373bf9f6a0662a720ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640276"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Asistente para componentes de páginas Active Server ATL

Use esta página del Asistente para componentes de páginas Active Server ATL para especificar la configuración opcional para controlar la información y estado relacionados con el componente ASP.

- **Métodos opcionales**

   Agrega los métodos ASP opcionales, **OnStartPage** y **OnEndPage**, al objeto. Esta opción debe seleccionarse para establecer los objetos intrínsecos de páginas Active Server. De forma predeterminada, se selecciona.

- **OnStartPage/OnEndPage**

   [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx) se llama a la primera vez que el script intenta tener acceso al objeto. **OnEndPage** se llama cuando finaliza el objeto de la secuencia de comandos de procesamiento.

- **Objeto intrínseco**

   Debe seleccionar la **OnStartPage/OnEndPage** opción para establecer los objetos intrínsecos de ASP.

|Opción|Descripción|
|------------|-----------------|
|**Solicitud**|Proporciona acceso a las páginas Active Server intrínseco **solicitar** objeto. El objeto de solicitud se utiliza para pasar una solicitud HTTP.|
|**Respuesta**|Proporciona acceso a las páginas Active Server intrínseco **respuesta** objeto. En respuesta a una solicitud, el objeto de respuesta envía información al explorador para mostrar al usuario.|
|**Sesión**|Proporciona acceso a las páginas Active Server intrínseco **sesión** objeto. El **sesión** objeto mantiene información acerca de la sesión actual del usuario, almacenar y recuperar información de estado.|
|**Aplicación**|Proporciona acceso a las páginas Active Server intrínseco **aplicación** objeto. El **aplicación** objeto administra el estado que se comparte entre varios objetos ASP.|
|**Servidor**|Proporciona acceso a las páginas Active Server intrínseco **Server** objeto. El **Server** objeto le permite crear otros objetos ASP.|

## <a name="see-also"></a>Vea también

[Asistente para componentes de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Componente de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

