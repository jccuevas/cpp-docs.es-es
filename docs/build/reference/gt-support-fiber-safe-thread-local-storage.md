---
title: -GT (admitir el almacenamiento Local de subprocesos para fibra) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
dev_langs: C++
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86c027a1796f42d7b2932f68aff00136ee0d217f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (Admitir el almacenamiento local de subprocesos para fibra)
Admite la seguridad de fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos, es decir, datos asignados con `__declspec(thread)`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/GT  
```  
  
## <a name="remarks"></a>Comentarios  
 Datos que se declaran con `__declspec(thread)` hace referencia a través de una matriz de almacenamiento local de subprocesos (TLS). La matriz TLS es una matriz de direcciones que el sistema mantiene para cada subproceso. Cada dirección de esta matriz proporciona la ubicación de los datos de almacenamiento local de subprocesos.  
  
 Una fibra es un objeto ligero que consta de una pila y un contexto de registro y se puede programar en varios subprocesos. Una fibra puede ejecutarse en cualquier subproceso. Dado que una fibra puede intercambiar y después reiniciarla en otro subproceso, la dirección de la matriz TLS no debe almacenado en memoria caché ni optimizarse como una subexpresión común a través de una llamada de función (vea la [/Og (optimizaciones globales)](../../build/reference/og-global-optimizations.md) opción detalles). **/GT** evita estas optimizaciones.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **optimización** página de propiedades.  
  
4.  Modificar el **habilitar optimizaciones para fibra** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)