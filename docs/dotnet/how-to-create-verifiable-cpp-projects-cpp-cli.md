---
title: "Cómo: crear proyectos de C++ comprobables (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d6a7806183766d96c0d106d9d9e890b046f4563
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Cómo: Crear proyectos de C++ comprobables (C++/CLI)
Asistentes para aplicaciones de visuales C++ no crean proyectos comprobables, pero se pueden convertir proyectos para que sea comprobable. En este tema se describe cómo establecer propiedades del proyecto y modificar archivos de código fuente del proyecto para transformar los proyectos de Visual C++ para generar aplicaciones comprobables.  
  
## <a name="compiler-and-linker-settings"></a>Configuración del compilador y del vinculador  
 De forma predeterminada, los proyectos de .NET use la marca de compilador /clr y configuran al vinculador para hardware de destino x86. Para código comprobable, debe usar el indicador/clr: safe e indicar al vinculador que genere MSIL en lugar de instrucciones máquina nativas.  
  
#### <a name="to-change-the-compiler-and-linker-settings"></a>Para cambiar la configuración de compilador y el vinculador  
  
1.  Mostrar la página de propiedades del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
2.  En el **General** página en el **propiedades de configuración** de conjunto de nodos, el **soporte de Common Language Runtime** propiedad a **seguro MSIL Common Language Compatibilidad en tiempo de ejecución (/ CLR: safe)**.  
  
3.  En el **avanzadas** página en el **vinculador** de conjunto de nodos, el **tipo de imagen CLR** propiedad **Forzar imagen de IL segura (/ CLRIMAGETYPE: safe)**.  
  
## <a name="removing-native-data-types"></a>Quitar tipos de datos nativos  
 Dado que los tipos de datos nativos no son comprobables, incluso si no se usan realmente, debe quitar todos los archivos de encabezado que contiene los tipos nativos.  
  
> [!NOTE]
>  El siguiente procedimiento se aplica a los proyectos de aplicación de Windows Forms (. NET) y aplicación de consola (. NET).  
  
#### <a name="to-remove-references-to-native-data-types"></a>Para quitar las referencias a tipos de datos nativos  
  
1.  Marque como comentario todo el archivo Stdafx.h.  
  
## <a name="configuring-an-entry-point"></a>Configurar un punto de entrada  
 Dado que las aplicaciones comprobables no pueden usar las bibliotecas de tiempo de ejecución de C (CRT), no pueden depender de CRT para llamar a la función principal como punto de entrada estándar. Esto significa que debe proporcionar explícitamente el nombre de la función llamar inicialmente al vinculador. (En este caso, Main() se utiliza en lugar de main() o _tmain () para indicar un punto de entrada de CRT no, pero dado que el punto de entrada debe especificarse explícitamente, este nombre es arbitrario.)  
  
> [!NOTE]
>  Los procedimientos siguientes se aplican a los proyectos de aplicación de consola (. NET).  
  
#### <a name="to-configure-an-entry-point"></a>Para configurar un punto de entrada  
  
1.  Cambie _tmain () por Main() en el archivo del proyecto .cpp principal.  
  
2.  Mostrar la página de propiedades del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
3.  En el **avanzadas** página en el **vinculador** nodo, escriba `Main` como el **punto de entrada** valor de propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)