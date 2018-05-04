---
title: Compatibilidad de ATL con controles DHTML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f57fc841ba2eb3473ccb866df7333ebd24583d40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="atl-support-for-dhtml-controls"></a>Compatibilidad de ATL con controles DHTML
Con ATL, puede crear un control con capacidad de HTML dinámico (DHTML). Un control DHTML ATL:  
  
-   Hospede el control WebBrowser.  
  
-   Especifica, mediante HTML, la interfaz de usuario (UI) del control DHTML.  
  
-   Tiene acceso al objeto WebBrowser y sus métodos a través de su interfaz, [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx).  
  
-   Administra la comunicación entre el código de C++ y HTML.  
  
 Un control DHTML es similar a cualquier otro control ATL, excepto el control DHTML incluye una interfaz de envío adicionales. Consulte la figura en [identifica los elementos del proyecto de Control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) para ver una ilustración de las interfaces proporcionadas en el proyecto DHTML predeterminado.  
  
 Puede ver el control DHTML ATL en un explorador Web o en otro contenedor, como ActiveX Control Test Container.  
  
## <a name="in-this-section"></a>En esta sección  
 [Identificar los elementos del proyecto de control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md)  
 Describe los elementos de un proyecto de control DHTML.  
  
 [Llamar al código C++ desde DHTML](../atl/calling-cpp-code-from-dhtml.md)  
 Proporciona un ejemplo de llamar a código de C++ desde un control DHTML.  
  
 [Crear un control DHTML ATL](../atl/creating-an-atl-dhtml-control.md)  
 Se enumeran los pasos para crear un control DHTML.  
  
 [Probar el control DHTML ATL](../atl/testing-the-atl-dhtml-control.md)  
 Muestra cómo compilar y probar el proyecto de control DHTML inicial.  
  
 [Modificar el control DHTML ATL](../atl/modifying-the-atl-dhtml-control.md)  
 Muestra cómo agregar alguna funcionalidad al control.  
  
 [Probar el Control DHTML ATL modificado](../atl/testing-the-modified-atl-dhtml-control.md)  
 Muestra cómo compilar y probar la funcionalidad del control agregado.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.

