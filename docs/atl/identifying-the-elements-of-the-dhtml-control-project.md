---
title: Identificación de los elementos del proyecto de control DHTML
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 5fabdc815989c21bdf6b0932b9d6826e28d7012a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319498"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identificación de los elementos del proyecto de control DHTML

La mayoría del código de control DHTML es exactamente igual que el creado para cualquier control ATL. Para una comprensión básica del código genérico, consulte el [tutorial ATL](../atl/active-template-library-atl-tutorial.md)y lea las secciones Creación de [un proyecto ATL](../atl/reference/creating-an-atl-project.md) y [Fundamentos de objetos COM ATL](../atl/fundamentals-of-atl-com-objects.md).

Un control DHTML es similar a cualquier control ATL, excepto:

- Además de las interfaces normales que implementa un control, implementa una interfaz adicional que se utiliza para comunicarse entre el código C++ y la interfaz de usuario (UI) HTML. La interfaz de usuario HTML llama al código C++ mediante esta interfaz.

- Crea un recurso HTML para la interfaz de usuario del control.

- Permite el acceso al modelo de objetos DHTML a través de la variable `m_spBrowser`miembro , que es un puntero inteligente de tipo [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)). Utilice este puntero para tener acceso a cualquier parte del modelo de objetos DHTML.

El gráfico siguiente ilustra la relación entre el archivo DLL, el control DHTML, el explorador web y el recurso HTML.

![Elementos de un proyecto de control DHTML](../atl/media/vc52en1.gif "Elementos de un proyecto de control DHTML")

> [!NOTE]
> Los nombres de este gráfico son marcadores de posición. Los nombres del recurso HTML y las interfaces expuestas en el control se basan en los nombres que se asignan en el Asistente para controles ATL.

En este gráfico, los elementos son:

- **Mi DLL** El archivo DLL creado mediante el Asistente para proyectos ATL.

- **Control DHTML** (`m_spBrowser`) El control DHTML, creado mediante el Asistente para objetos ATL. Este control accede al objeto del explorador web y sus `IWebBrowser2`métodos a través de la interfaz del objeto del explorador web, . El propio control expone las dos interfaces siguientes, además de las otras interfaces estándar necesarias para un control.

  - `IDHCTL1`La interfaz expuesta por el control para su uso únicamente por el contenedor.

  - `IDHCTLUI1`La interfaz de envío para la comunicación entre el código C+ + y la interfaz de usuario HTML. El explorador web utiliza la interfaz de envío del control para mostrar el control. Puede llamar a varios métodos de esta interfaz de `window.external`envío desde la interfaz de usuario del control invocando , seguido por el nombre del método en esta interfaz de envío que desea invocar. Tendría acceso `window.external` desde una etiqueta SCRIPT dentro del HTML que constituye la interfaz de usuario para este control. Para obtener más información acerca de cómo invocar métodos externos en el archivo de recursos, vea [llamar a código C++ desde DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** El identificador de recurso del recurso HTML. Su nombre de archivo, en este caso, es DHCTL1UI.htm. El control DHTML utiliza un recurso HTML que contiene etiquetas HTML estándar y comandos de envío de ventanas externas que puede editar mediante el editor de texto.

- **Navegador web** El explorador web muestra la interfaz de usuario del control, en función del código HTML del recurso HTML. Un puntero a la `IWebBrowser2` interfaz del explorador web está disponible en el control DHTML para permitir el acceso al modelo de objetos DHTML.

El Asistente para controles ATL genera un control con código predeterminado tanto en el recurso HTML como en el archivo .cpp. Puede compilar y ejecutar el control según lo generado por el asistente y, a continuación, ver el control en el explorador web o el contenedor de prueba de control ActiveX. La imagen siguiente muestra el control DHTML ATL predeterminado con tres botones que se muestran en contenedor de pruebas:

![Control DHTML ATL](../atl/media/vc52en2.gif "Control DHTML ATL")

Consulte [Creación de un control DHTML ATL](../atl/creating-an-atl-dhtml-control.md) para empezar a crear un control DHTML. Consulte [Probar propiedades y eventos con contenedor](../mfc/testing-properties-and-events-with-test-container.md) de pruebas para obtener información sobre cómo obtener acceso al contenedor de pruebas.

## <a name="see-also"></a>Consulte también

[Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)
