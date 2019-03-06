---
title: /GT (Admitir el almacenamiento local de subprocesos para fibra)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
ms.openlocfilehash: 14d2f66401b7b7ed324b79b12b6de26c7ee450b2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420263"
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
