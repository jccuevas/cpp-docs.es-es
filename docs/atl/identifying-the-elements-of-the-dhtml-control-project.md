---
title: Identificar los elementos del proyecto de Control DHTML
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 32b1c00e3ad3ed15fa56f7718789fe1a2e3ecbab
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424384"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identificar los elementos del proyecto de Control DHTML

La mayoría del código DHTML control exactamente como el que se crea para cualquier control ATL. Para obtener un conocimiento básico del código genérico, funcionan a través de la [tutorial de ATL](../atl/active-template-library-atl-tutorial.md), y lea las secciones [crear un proyecto ATL](../atl/reference/creating-an-atl-project.md) y [aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md).

Un control DHTML es similar a cualquier control ATL, excepto:

- Además de las interfaces estándar que implementa un control, implementa una interfaz adicional que se usa para la comunicación entre el código de C++ y la interfaz de usuario (UI) de HTML. La interfaz de usuario HTML llama a código de C++ mediante esta interfaz.

- Crea un recurso HTML para el control de interfaz de usuario.

- Permite el acceso al modelo de objetos DHTML a través de la variable miembro `m_spBrowser`, que es un puntero inteligente de tipo [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)). Use este puntero para tener acceso a cualquier parte del modelo de objetos DHTML.

El siguiente gráfico ilustra la relación entre el archivo DLL, el control DHTML, el explorador Web y el recurso HTML.

![Elementos de un proyecto de control DHTML](../atl/media/vc52en1.gif "elementos de un proyecto de control DHTML")

> [!NOTE]
>  Los nombres de este gráfico son marcadores de posición. Los nombres de los recursos HTML y las interfaces expuestas en el control se basan en los nombres que se les asigna en el Asistente para controles ATL.

En este gráfico, los elementos son:

- **Mi DLL** la DLL creadas con el Asistente para proyectos ATL.

- **Control DHTML** (`m_spBrowser`) el control DHTML, creado mediante el Asistente para objetos ATL. Este control tiene acceso a sus métodos y el objeto de explorador Web a través de la interfaz del objeto de explorador Web, `IWebBrowser2`. El propio control expone las dos interfaces siguientes, además de las demás interfaces estándar requeridas para un control.

   - `IDHCTL1` La interfaz expuesta por el control para su uso exclusivo por el contenedor.

   - `IDHCTLUI1` La interfaz de envío para la comunicación entre el código de C++ y la interfaz de usuario HTML. El explorador Web utiliza la interfaz de envío del control para mostrar el control. Se pueden llamar a varios métodos de esta interfaz de envío desde la interfaz de usuario del control mediante la invocación `window.external`, seguido por el nombre del método en la interfaz de envío que desea invocar. Para acceder a `window.external` desde una etiqueta de SCRIPT en el código HTML que compone la interfaz de usuario para este control. Para obtener más información sobre cómo invocar métodos externos en el archivo de recursos, consulte [llamar a código de C++ desde DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** el identificador de recurso del recurso HTML. Su nombre de archivo, en este caso, es DHCTL1UI.htm. El control DHTML utiliza un recurso HTML que contiene etiquetas HTML estándar y enviar comandos de ventana externo que se pueden editar con el editor de texto.

- **Explorador Web** el explorador Web muestra la interfaz de usuario del control, según el código HTML en el recurso de HTML. Un puntero en el explorador Web `IWebBrowser2` interfaz está disponible en el control DHTML para permitir el acceso al modelo de objetos DHTML.

El Asistente para controles ATL genera un control con el código de forma predeterminada en el recurso HTML y el archivo. cpp. Puede compilar y ejecutar el control como el generado por el asistente y, a continuación, el control de vista en el explorador Web o el Control ActiveX Test Container. La siguiente imagen muestra el control DHTML ATL predeterminado con tres botones en el contenedor de prueba:

![Control DHTML ATL](../atl/media/vc52en2.gif "control DHTML ATL")

Consulte [crear un Control de DHTML ATL](../atl/creating-an-atl-dhtml-control.md) para empezar a crear un control DHTML. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo obtener acceso a Test Container.

## <a name="see-also"></a>Vea también

[Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)
