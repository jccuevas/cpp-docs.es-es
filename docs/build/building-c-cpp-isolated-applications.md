---
title: "Aplicaciones aisladas de compilación de C/C ++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76b0c1fa5b509ae495a12fb63164d7da01f402aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="building-cc-isolated-applications"></a>Compilar aplicaciones aisladas de C/C++
Una aplicación aislada sólo depende de ensamblados en paralelo y enlaza a sus dependencias mediante un manifiesto. No es necesaria para la aplicación sea completamente aislado para poder ejecutarse correctamente en Windows; Sin embargo, al invertir en aislar totalmente su aplicación, puede ahorrar tiempo si tiene que mantener la aplicación en el futuro. Para obtener más información sobre las ventajas de aislar totalmente su aplicación, consulte [aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190).  
  
 Cuando se compila la aplicación de C o C++ nativo con Visual C++, de forma predeterminada, Visual Studio sistema del proyecto genera un archivo de manifiesto que describe las dependencias de la aplicación en las bibliotecas de Visual C++. Si se trata de las dependencias sola tiene la aplicación, a continuación, se convierte en una aplicación aislada en cuanto se vuelve a generar con Visual Studio. Si la aplicación utiliza otras bibliotecas en tiempo de ejecución, puede que necesite volver a generar las bibliotecas como ensamblados en paralelo siguiendo los pasos descritos en [creación de ensamblados de C o C++-paralelo](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de aplicaciones aisladas y ensamblados en paralelo](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)