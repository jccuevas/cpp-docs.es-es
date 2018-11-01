---
title: /vd (Deshabilitar desplazamientos de constructores)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: 229306fe93dedcf5c87d53e2227c8f17baef07c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652964"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Deshabilitar desplazamientos de constructores)

## <a name="syntax"></a>Sintaxis

```
/vdn
```

## <a name="arguments"></a>Argumentos

**0**<br/>
Suprime al miembro de desplazamiento del constructor o destructor de vtordisp. Elija esta opción solo si está seguro de que todos los constructores de clase y los destructores llaman virtuales funciona prácticamente.

**1**<br/>
Permite la creación de los miembros de desplazamiento del constructor o destructor de vtordisp ocultos. Esta opción es el valor predeterminado.

**2**<br/>
Le permite usar [dynamic_cast (operador)](../../cpp/dynamic-cast-operator.md) en un objeto que se está construyendo. Por ejemplo, un dynamic_cast de una clase base virtual a una clase derivada.

**/ vd2** agrega un campo vtordisp cuando tenga una base virtual con funciones virtuales. **/ vd1** debería ser suficiente. La más común caso where **/vd2** es necesario es cuando la función virtual solo en la base virtual es un destructor.

## <a name="remarks"></a>Comentarios

Estas opciones se aplican únicamente al código de C++ que usa bases virtuales.

Visual C++ implementa la capacidad de desplazamiento de construcción de C++ en situaciones donde se usa la herencia virtual. Desplazamientos de constructores solucionar el problema que se crea cuando una función virtual, declarada en una base virtual y se reemplaza en una clase derivada, se llama desde un constructor durante la construcción de una clase derivada posterior.

El problema es que la función virtual se puede pasar una incorrecta `this` puntero como resultado discrepancias entre los desplazamientos de virtual de las bases de una clase y los desplazamientos de sus clases derivadas. La solución proporciona un ajuste de desplazamiento de construcción único, denominado campo vtordisp, para cada base de una clase virtual.

De forma predeterminada, se introducen vtordisp (campos) cada vez que el código define los destructores y constructores definidos por el usuario y también reemplaza a funciones virtuales de bases virtuales.

Estas opciones afectan a los archivos de código fuente. Use [vtordisp](../../preprocessor/vtordisp.md) suprimir y, a continuación, volver a habilitar los campos de vtordisp clase por clase.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)