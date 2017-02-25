---
title: "Plantilla de proyecto de Biblioteca de clases de WRL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 628b0852-89e5-44f8-bf58-a09762bda15c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Plantilla de proyecto de Biblioteca de clases de WRL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si utiliza Visual Studio para escribir un proyecto de [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\), puede simplificar en gran medida la tarea descargar la plantilla de proyecto biblioteca de clases de WRL.  
  
> [!NOTE]
>  Si tiene que actualizar manualmente las configuraciones de proyecto para un proyecto existente, vea [Archivos DLL \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh699881\(v=vs.110\).aspx).  
  
## Descargar la plantilla de proyecto de WRL  
 Visual Studio no proporciona una plantilla para los proyectos de [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] .  Aquí es cómo descargar una plantilla de proyecto que cree una biblioteca de clases básica para las aplicaciones de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] con [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)].  
  
#### Para descargar la plantilla de proyecto de WRL  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo proyecto**.  
  
2.  En el panel izquierdo del cuadro de diálogo de **Nuevo proyecto** , de **Con conexión**seleccione, y de **Plantillas**seleccione.  
  
3.  En el cuadro de **Plantillas en línea de búsqueda** en la esquina superior derecha, `Biblioteca de clases de WRL`escrito.  Cuando la plantilla aparece en los resultados de la búsqueda, elija el botón de **Aceptar** .  
  
4.  En el cuadro de diálogo de **Descargar e instalar** , si está de acuerdo los términos de licencia, elija el botón de **Instalación** .  
  
5.  Después de las instalaciones de la plantilla, crean un proyecto eligiendo **archivo**, **Nuevo proyecto**, y la selección de la plantilla de `WRLClassLibrary` .  El proyecto crea un archivo DLL.  
  
## Ejemplos que utilizan la plantilla de proyecto  
 Lea [Tutorial: Crear un componente básico de Windows en tiempo de ejecución](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md) para obtener un ejemplo que utilice esta plantilla para crear un componente de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] .  
  
## La plantilla de proyecto proporciona  
 La plantilla de proyecto proporciona:  
  
-   un archivo .idl que declara los atributos de MIDL para una interfaz básica la implementación de la clase.  Por ejemplo:  
  
     [!code-cpp[wrl-project-template#1](../windows/codesnippet/CPP/wrl-class-library-project-template_1.idl)]  
  
-   un archivo .cpp que define la implementación de la clase.  Por ejemplo:  
  
     [!code-cpp[wrl-project-template#2](../windows/codesnippet/CPP/wrl-class-library-project-template_2.cpp)]  
  
     Ayuda de la clase base de [RuntimeClass](../windows/runtimeclass-class.md) administran la referencia global de todos los objetos del módulo y declaran los métodos de las interfaces de [IUnknown](http://msdn.microsoft.com/es-es/33f1d79a-33fc-4ce5-a372-e08bda378332) y de [IInspectable](http://msdn.microsoft.com/es-es/0657e51f-d4c0-46c6-927d-b01e54b6846c) .  La macro de [InspectableClass](../windows/inspectableclass-macro.md) implementa `IUnknown` y `IInspectable`.  La macro de [ActivatableClass](../Topic/ActivatableClass%20Macros.md) crea un generador de clases que cree instancias de la clase.  
  
-   un archivo denominado module.cpp que define las exportaciones `DllMain`, `DllCanUnloadNow`, `DllGetActivationFactory`, y `DllGetClassObject`de biblioteca.  
  
## Vea también  
 [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md)