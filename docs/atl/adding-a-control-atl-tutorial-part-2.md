---
title: Agregar un Control (ATL Tutorial, parte 2) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: get-started-article
dev_langs:
- C++
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6bedc0fbe4cd1e4a612bcb329071668e783b3de8
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Agregar un control (Tutorial de ATL, Parte 2)
En este paso, agregará un control al proyecto, lo compilará y lo probará en una página web.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-add-an-object-to-an-atl-project"></a>Para agregar un objeto a un proyecto ATL  
  
1.  En la Vista de clases, haga clic con el botón secundario en el proyecto Polygon.  
  
2.  Seleccione **agregar** en el menú contextual y haga clic en **nuevo elemento** en el submenú.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**. Las distintas categorías de objetos se enumeran en la estructura de árbol a la izquierda.  
  
3.  Haga clic en el **ATL** carpeta.  
  
4.  En la lista de plantillas de la derecha, seleccione **Control ATL**. Haga clic en **Agregar**. El Asistente para controles ATL se abrirá y podrá configurar el control.  
  
5.  Tipo `PolyCtl` como nombre corto y observe que los demás campos se completan automáticamente. No haga clic en **finalizar** todavía, porque tiene que realizar algunos cambios.  
  
 Del Asistente para controles ATL **nombres** página contiene los siguientes campos:  
  
|Campo|Contenido|  
|-----------|--------------|  
|**Nombre corto**|El nombre que especificó para el control.|  
|**Clase**|El nombre de la clase de C++ creada para implementar el control.|  
|**archivo .h**|El archivo creado para contener la definición de la clase de C++.|  
|**archivo .cpp**|El archivo creado para contener la implementación de la clase de C++.|  
|**CoClass**|Nombre de la clase de componente para este control.|  
|**Interface**|El nombre de la interfaz donde el control implementará sus métodos y propiedades personalizados.|  
|**Type**|Una descripción del control.|  
|**ProgID**|El nombre legible que se puede utilizar para buscar el CLSID del control.|  
  
 Debe configurar varias opciones adicionales en el Asistente para controles ATL.  
  
#### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Para habilitar la compatibilidad con la información de error enriquecida y con los puntos de conexión  
  
1.  Haga clic en **opciones** para abrir el **opciones** página.  
  
2.  Seleccione el **puntos de conexión** casilla de verificación. De esta forma se creará la compatibilidad con una interfaz de salida en el archivo IDL.  
  
 También puede hacer que el control sea insertable, es decir, que se pueda incrustar en las aplicaciones que admiten objetos incrustados, como Excel o Word.  
  
#### <a name="to-make-the-control-insertable"></a>Para que el control se pueda insertar  
  
1.  Haga clic en **apariencia** para abrir el **apariencia** página.  
  
2.  Seleccione el **Insertable** casilla de verificación.  
  
 El polígono mostrado por el objeto tendrá un color de relleno sólido, por lo que debe agregar una propiedad estándar `Fill Color`.  
  
#### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Para agregar una propiedad estándar Color de relleno y crear el control  
  
1.  Haga clic en **propiedades estándar** para abrir el **propiedades estándar** página.  
  
2.  En **no admite**, desplácese hacia abajo en la lista de propiedades estándar posibles. Haga doble clic en `Fill Color` para moverla a la **Supported** lista.  
  
3.  Esto completa las opciones para el control. Haga clic en **Finalizar**.  
  
 Cuando el asistente creó el control, se produjeron varios cambios de código y se agregaron archivos. Se crearon los siguientes archivos:  
  
|Archivo|Descripción|  
|----------|-----------------|  
|PolyCtl.h|Contiene la mayor parte de la implementación de la clase `CPolyCtl` de C++.|  
|PolyCtl.cpp|Contiene los elementos restantes de `CPolyCtl`.|  
|PolyCtl.rgs|Un archivo de texto que contiene el script del Registro utilizado para registrar el control.|  
|PolyCtl.htm|Una página web que contiene una referencia al control recién creado.|  
  
 El asistente también realizó los siguientes cambios de código:  
  
-   Agregó una instrucción `#include` a los archivos stdafx.h y stdafx.cpp para incluir los archivos ATL necesarios para admitir controles.  
  
-   Cambió Polygon.idl para incluir los detalles del nuevo control.  
  
-   Agregó el nuevo control al mapa de objetos en Polygon.cpp.  
  
 Ahora puede compilar el control para verlo en acción.  
  
## <a name="building-and-testing-the-control"></a>Compilar y probar el control  
  
#### <a name="to-build-and-test-the-control"></a>Para compilar y probar el control  
  
1.  En el **generar** menú, haga clic en **Generar Polygon**.  
  
     Una vez que termina la generación de control, haga clic en PolyCtl.htm en **el Explorador de soluciones** y seleccione **ver en el explorador**. Se mostrará la página web HTML que contiene el control. Debería ver una página con el título "Página ATL 8.0 de prueba para el objeto PolyCtl" y el texto **PolyCtl**. Este es su control.  
  
> [!NOTE]
>  Cuando complete este tutorial, si recibe un mensaje de error acerca de que el archivo DLL no se puede crear, cierre el archivo PolyCtl.htm y ActiveX Control Test Container, y compile de nuevo la solución. Si aún no puede crear el archivo DLL, reinicie el equipo o cierre la sesión (si utiliza Terminal Services).  
  
 A continuación, agregará una propiedad personalizada al control.  
  
 [Vuelva al paso 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [al paso 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)

