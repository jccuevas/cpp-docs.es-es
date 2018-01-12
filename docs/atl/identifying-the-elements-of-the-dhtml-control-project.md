---
title: Identificar los elementos del proyecto de Control DHTML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 74b271f56fe7c8d3345ce53de06a18a2700175f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identificar los elementos del proyecto de Control DHTML
La mayoría del código control DHTML es exactamente igual al creado para cualquier control ATL. Para obtener una comprensión básica del código genérico, examine la [tutorial ATL](../atl/active-template-library-atl-tutorial.md), y lea las secciones [crear un proyecto ATL](../atl/reference/creating-an-atl-project.md) y [aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md).  
  
 Un control DHTML es similar a cualquier control ATL, excepto:  
  
-   Además de las interfaces estándar que implementa un control, implementa una interfaz adicional que se utiliza para la comunicación entre el código de C++ y la interfaz de usuario (UI) de HTML. La interfaz de usuario HTML llama al código de C++ mediante esta interfaz.  
  
-   Crea un recurso HTML para el control de interfaz de usuario.  
  
-   Permitir el acceso al modelo de objetos DHTML a través de la variable miembro `m_spBrowser`, que es un puntero inteligente de tipo [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx). Utilice este puntero para tener acceso a cualquier parte del modelo de objetos DHTML.  
  
 El siguiente gráfico ilustra la relación entre el archivo DLL, el control DHTML, el explorador Web y el recurso HTML.  
  
 ![Elementos de un proyecto de control DHTML](../atl/media/vc52en1.gif "vc52en1")  
  
> [!NOTE]
>  Los nombres de este gráfico son marcadores de posición. Los nombres de los recursos HTML y las interfaces expuestas en el control se basan en los nombres que se les asigna en el Asistente para controles ATL.  
  
 En este gráfico, los elementos son:  
  
-   **El archivo DLL** el archivo DLL creado mediante el Asistente para proyectos ATL.  
  
-   **Control DHTML** (`m_spBrowser`) el control DHTML, creado con el Asistente para objetos ATL. Este control tiene acceso a sus métodos y el objeto de explorador Web a través de la interfaz del objeto de explorador Web, **IWebBrowser2**. El propio control expone las dos interfaces siguientes, además de las demás interfaces estándar requeridas para un control.  
  
    -   **IDHCTL1** la interfaz expuesta por el control para su uso exclusivo por el contenedor.  
  
    -   **IDHCTLUI1** la interfaz de envío para la comunicación entre el código de C++ y la interfaz de usuario HTML. El explorador Web usa la interfaz de envío del control para mostrar el control. Se pueden llamar a varios métodos de esta interfaz de envío de la interfaz de usuario del control mediante la invocación de `window.external`, seguido del nombre de método en la interfaz de envío que desea invocar. Se obtiene acceso a `window.external` de una etiqueta SCRIPT en el código HTML que compone la interfaz de usuario para este control. Para obtener más información sobre cómo invocar métodos externos en el archivo de recursos, consulte [llamar a código de C++ desde DHTML](../atl/calling-cpp-code-from-dhtml.md).  
  
-   **IDR_CTL1** el identificador de recurso del recurso HTML. Su nombre de archivo, en este caso, es DHCTL1UI.htm. El control DHTML utiliza un recurso HTML que contiene etiquetas HTML estándar y los comandos de envío de ventana externos que se pueden editar con el editor de texto.  
  
-   **Explorador Web** el explorador Web muestra la interfaz de usuario del control, según el código HTML en el recurso HTML. Un puntero en el explorador Web **IWebBrowser2** interfaz está disponible en el control DHTML para permitir el acceso al modelo de objetos DHTML.  
  
 El Asistente para controles ATL genera un control con código predeterminado en el recurso HTML y el archivo .cpp. Puede compilar y ejecutar el control como el generado por el asistente y, a continuación, ver el control en el explorador Web o el Control ActiveX Test Container. La figura siguiente muestra el control DHTML ATL predeterminado con tres botones que se muestran en el contenedor de prueba:  
  
 ![Control DHTML ATL](../atl/media/vc52en2.gif "vc52en2")  
  
 Vea [crear un Control de DHTML ATL](../atl/creating-an-atl-dhtml-control.md) para empezar a compilar un control DHTML. Vea [Probar propiedades y eventos con Test Container](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo obtener acceso a Test Container.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)

