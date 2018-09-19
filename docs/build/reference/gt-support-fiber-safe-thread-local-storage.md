---
title: -GT (admitir el almacenamiento Local de subprocesos para fibra) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
dev_langs:
- C++
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eeec9ddce36777fc6fcb15b30a864f1c04a7b09b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700848"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (Admitir el almacenamiento local de subprocesos para fibra)

Admite la seguridad de fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos, es decir, los datos asignados con `__declspec(thread)`.

## <a name="syntax"></a>Sintaxis

```
/GT
```

## <a name="remarks"></a>Comentarios

Datos que se declaran con `__declspec(thread)` se hace referencia a través de una matriz de almacenamiento local de subprocesos (TLS). La matriz TLS es una matriz de direcciones que el sistema mantiene para cada subproceso. Cada dirección de esta matriz proporciona la ubicación de los datos de almacenamiento local de subprocesos.

Una fibra es un objeto ligero que consta de una pila y un contexto de registro y puede programarse en varios subprocesos. Una fibra puede ejecutarse en cualquier subproceso. Dado que una fibra puede suspender y reinicia más tarde en un subproceso diferente, la dirección de la matriz TLS no debe almacenar en caché u optimizarse como una subexpresión común a través de una llamada de función (consulte la [/Og (optimizaciones globales)](../../build/reference/og-global-optimizations.md) opción detalles). **/GT** evita estas optimizaciones.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **optimización** página de propiedades.

1. Modificar el **habilitar optimizaciones para fibra** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)