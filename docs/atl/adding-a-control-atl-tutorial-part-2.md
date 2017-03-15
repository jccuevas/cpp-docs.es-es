---
title: "Agregar un control (Tutorial de ATL, Parte 2) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Agregar un control (Tutorial de ATL, Parte 2)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este paso, agregará un control al proyecto, lo compilará y lo probará en una página web.  
  
## Procedimientos  
  
#### Para agregar un objeto a un proyecto ATL  
  
1.  En la Vista de clases, haga clic con el botón secundario en el proyecto Polygon.  
  
2.  Señale **Agregar** en el menú contextual y haga clic en **Clase** en el submenú.  
  
     Aparecerá el cuadro de diálogo **Agregar clase**.  Las distintas categorías de objetos se enumeran en la estructura de árbol a la izquierda.  
  
3.  Haga clic en la carpeta **ATL**.  
  
4.  En la lista de plantillas de la derecha, seleccione **Control ATL**.  Haga clic en **Agregar**.  El Asistente para controles ATL se abrirá y podrá configurar el control.  
  
5.  Escriba `PolyCtl` como nombre corto y observe que los demás campos se completan automáticamente.  No haga clic en **Finalizar** todavía, porque hay que realizar algunos cambios.  
  
 La página **Nombres** del Asistente para controles ATL contiene los siguientes campos:  
  
|Campo|Contenido|  
|-----------|---------------|  
|**Nombre corto**|El nombre que especificó para el control.|  
|**Clase**|El nombre de la clase de C\+\+ creada para implementar el control.|  
|**Archivo .h**|El archivo creado para contener la definición de la clase de C\+\+.|  
|**Archivo .cpp**|El archivo creado para contener la implementación de la clase de C\+\+.|  
|**CoClass**|Nombre de la clase de componente para este control.|  
|**Interfaz**|El nombre de la interfaz donde el control implementará sus métodos y propiedades personalizados.|  
|**Tipo**|Una descripción del control.|  
|**Id. de programa**|El nombre legible que se puede utilizar para buscar el CLSID del control.|  
  
 Debe configurar varias opciones adicionales en el Asistente para controles ATL.  
  
#### Para habilitar la compatibilidad con la información de error enriquecida y con los puntos de conexión  
  
1.  Haga clic en **Opciones** para abrir la página **Opciones**.  
  
2.  Active la casilla **Puntos de conexión**.  De esta forma se creará la compatibilidad con una interfaz de salida en el archivo IDL.  
  
 También puede hacer que el control sea insertable, es decir, que se pueda incrustar en las aplicaciones que admiten objetos incrustados, como Excel o Word.  
  
#### Para que el control se pueda insertar  
  
1.  Haga clic en **Apariencia** para abrir la página **Apariencia**.  
  
2.  Active la casilla **Insertable**.  
  
 El polígono mostrado por el objeto tendrá un color de relleno sólido, por lo que debe agregar una propiedad estándar `Fill Color`.  
  
#### Para agregar una propiedad estándar Color de relleno y crear el control  
  
1.  Haga clic en **Propiedades estándar** para abrir la página **Propiedades estándar**.  
  
2.  En **No compatible**, desplácese hacia abajo por la lista de propiedades estándar posibles.  Haga doble clic en `Fill Color` para moverlo a la lista **Compatible**.  
  
3.  Esto completa las opciones para el control.  Haga clic en **Finalizar**.  
  
 Cuando el asistente creó el control, se produjeron varios cambios de código y se agregaron archivos.  Se crearon los siguientes archivos:  
  
|Archivo|Descripción|  
|-------------|-----------------|  
|PolyCtl.h|Contiene la mayor parte de la implementación de la clase `CPolyCtl` de C\+\+.|  
|PolyCtl.cpp|Contiene los elementos restantes de `CPolyCtl`.|  
|PolyCtl.rgs|Un archivo de texto que contiene el script del Registro utilizado para registrar el control.|  
|PolyCtl.htm|Una página web que contiene una referencia al control recién creado.|  
  
 El asistente también realizó los siguientes cambios de código:  
  
-   Agregó una instrucción `#include` a los archivos stdafx.h y stdafx.cpp para incluir los archivos ATL necesarios para admitir controles.  
  
-   Cambió Polygon.idl para incluir los detalles del nuevo control.  
  
-   Agregó el nuevo control al mapa de objetos en Polygon.cpp.  
  
 Ahora puede compilar el control para verlo en acción.  
  
## Compilar y probar el control  
  
#### Para compilar y probar el control  
  
1.  En el menú **Compilar**, haga clic en **Compilar polígono**.  
  
     Una vez finalizada la compilación del control, haga clic con el botón secundario en PolyCtl.htm en el **Explorador de soluciones** y seleccione **Ver en el explorador**.  Se mostrará la página web HTML que contiene el control.  Debería aparecer una página con el título “Página de prueba de ATL 8.0 para el objeto PolyCtl” y el texto **PolyCtl**.  Este es su control.  
  
> [!NOTE]
>  Cuando complete este tutorial, si recibe un mensaje de error acerca de que el archivo DLL no se puede crear, cierre el archivo PolyCtl.htm y ActiveX Control Test Container, y compile de nuevo la solución.  Si aún no puede crear el archivo DLL, reinicie el equipo o cierre la sesión \(si utiliza Terminal Services\).  
  
 A continuación, agregará una propiedad personalizada al control.  
  
 [Volver al paso 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [Seguir con el paso 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)  
  
## Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)