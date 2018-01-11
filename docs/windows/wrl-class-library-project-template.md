---
title: Plantilla de proyecto de biblioteca de clases WRL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 628b0852-89e5-44f8-bf58-a09762bda15c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13fc476f696bdd2cb17ed58c496c63747db90322
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="wrl-class-library-project-template"></a>Plantilla de proyecto de Biblioteca de clases de WRL
Si usa Visual Studio para escribir un proyecto de biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución, puede simplificar en gran medida la tarea mediante la descarga de la plantilla de proyecto de biblioteca de clases de WRL.  
  
> [!NOTE]
>  Si tiene que actualizar manualmente la configuración del proyecto para un proyecto existente, vea [dll (C++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh699881\(v=vs.110\).aspx).  
  
## <a name="download-the-wrl-project-template"></a>Descargue la plantilla de proyecto WRL  
 Visual Studio no proporciona una plantilla para los proyectos de biblioteca de plantillas de C++ de Windows en tiempo de ejecución. Aquí se muestra cómo descargar una plantilla de proyecto que crea una biblioteca de clases básica para aplicaciones de la plataforma Universal de Windows con la biblioteca de plantillas de C++ de Windows en tiempo de ejecución.  
  
#### <a name="to-download-the-wrl-project-template"></a>Para descargar la plantilla de proyecto de WRL  
  
1.  En la barra de menús, elija **archivo**, **nuevo proyecto**.  
  
2.  En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, seleccione **en línea**y, a continuación, seleccione **plantillas**.  
  
3.  En el **buscar plantillas en línea** cuadro en la esquina superior derecha, tipo `WRL Class Library`. Cuando la plantilla aparece en los resultados de búsqueda, elija la **Aceptar** botón.  
  
4.  En el **descargar e instalar** términos de cuadro de diálogo, si está de acuerdo a la administración de licencias, elija la **instalar** botón.  
  
5.  Después de instala la plantilla, cree un proyecto seleccionando **archivo**, **nuevo proyecto**y, a continuación, seleccionando la `WRLClassLibrary` plantilla. El proyecto crea un archivo DLL.  
  
## <a name="examples-that-use-the-project-template"></a>Ejemplos que utilizan la plantilla de proyecto  
 Lectura [Tutorial: crear un componente básico de Windows en tiempo de ejecución](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md) para obtener un ejemplo que usa esta plantilla para crear un componente en tiempo de ejecución de Windows.  
  
## <a name="what-the-project-template-provides"></a>¿Qué proporciona la plantilla de proyecto  
 Proporciona la plantilla de proyecto:  
  
-   un archivo .idl que declara los atributos MIDL para una interfaz básica de su implementación de la clase. Por ejemplo:  
  
     [!code-cpp[wrl-project-template#1](../windows/codesnippet/CPP/wrl-class-library-project-template_1.idl)]  
  
-   un archivo .cpp que define la implementación de la clase. Por ejemplo:  
  
     [!code-cpp[wrl-project-template#2](../windows/codesnippet/CPP/wrl-class-library-project-template_2.cpp)]  
  
     El [RuntimeClass](../windows/runtimeclass-class.md) ayuda a administrar la referencia global de todos los objetos en el módulo de clase base y declara los métodos de la [IUnknown](http://msdn.microsoft.com/en-us/33f1d79a-33fc-4ce5-a372-e08bda378332) y [IInspectable](http://msdn.microsoft.com/en-us/0657e51f-d4c0-46c6-927d-b01e54b6846c) interfaces. El [InspectableClass](../windows/inspectableclass-macro.md) macro implementa `IUnknown` y `IInspectable`. El [ActivatableClass](../windows/activatableclass-macros.md) macro crea un generador de clases que crea instancias de la clase.  
  
-   exporta un archivo denominado module.cpp que define la biblioteca `DllMain`, `DllCanUnloadNow`, `DllGetActivationFactory`, y `DllGetClassObject`.  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)