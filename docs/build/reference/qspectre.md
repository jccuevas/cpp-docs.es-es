---
title: /Qspectre | Microsoft Docs
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec3509b71d78221c3e15607d34f674fc38d9f635
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43130994"
---
# <a name="qspectre"></a>/Qspectre

Especifica la generación del compilador de instrucciones para mitigar determinadas vulnerabilidades de seguridad de la variante 1 de Spectre.

## <a name="syntax"></a>Sintaxis

> **/Qspectre**

## <a name="remarks"></a>Comentarios

El **/qspectre** opción está disponible en Visual Studio 2017 versión 15.7 y versiones posteriores. Hace que el compilador inserta instrucciones para mitigar determinados [vulnerabilidades de seguridad de Spectre](https://spectreattack.com/spectre.pdf). Estas vulnerabilidades, llamadas *ataques de canal lateral de ejecución especulativa*, afectan a muchos sistemas operativos y los procesadores modernos, incluidos procesadores de Intel, AMD y ARM.

El **/qspectre** opción está desactivada de forma predeterminada.

En su versión inicial, el **/qspectre** opción solo funciona en código optimizado. Debe asegurarse de que al compilar el código con cualquiera de las opciones de optimización (por ejemplo, [/O2 o/O1](o1-o2-minimize-size-maximize-speed.md) pero no [/Od](od-disable-debug.md)) para asegurarse de que se aplica la mitigación. De forma similar, inspeccionar cualquier código que utilice [#pragma optimize ("stg", off)](../../preprocessor/optimize.md).

### <a name="applicability"></a>Aplicabilidad

Si el código funciona en los datos que se cruza un límite de confianza, a continuación, se recomienda que use el **/qspectre** opción recompilar y reimplementar el código para mitigar este problema tan pronto como sea posible. Código que carga la entrada de confianza que puede afectar a la ejecución de ejemplos de código que opera en datos que cruza un límite de confianza, por ejemplo, código que realice el procedimiento remoto llama, analiza la entrada no confiable o archivos o utiliza otros local entre procesos interfaces de comunicación entre procesos (IPC). Las técnicas estándar de espacio aislado no pueden ser suficientes. Debe investigar los espacios aislados cuidadosamente antes de decidir que el código no cruza un límite de confianza.

### <a name="availability"></a>Disponibilidad

El **/qspectre** opción está disponible en versión 15.5.5 de Visual Studio 2017 y todas las actualizaciones a los compiladores de Microsoft Visual C++ (MSVC) realizadas en o después del 23 de enero de 2018.

Todas las versiones de Visual Studio 2017 versión 15.5 y todas las versiones preliminares de Visual Studio versión 15.6 ya incluyen una opción sin documentar, **/d2guardspecload**, que es equivalente al comportamiento inicial de   **/qspectre**. Puede usar **/d2guardspecload** para aplicar la mismas mitigaciones a su código en estas versiones del compilador. Actualice la compilación para usar **/qspectre** en los compiladores que admiten la opción; la **/qspectre** opción también puede admitir las mitigaciones de nuevo en versiones posteriores del compilador.

### <a name="effect"></a>Efecto

El **/qspectre** opción genera código para mitigar la variante 1 de espectro omisión de comprobación de límites, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Funciona mediante la inserción de instrucciones que actúan como una barrera de ejecución especulativa de código. Las instrucciones específicas que se usa para mitigar la especulación de procesador dependen del procesador y su arquitectura de micro y pueden cambiar en futuras versiones del compilador.

Cuando el **/qspectre** opción está habilitada, el compilador intenta identificar instancias donde la ejecución especulativa puede omitir las comprobaciones de límites e inserta las instrucciones de barrera. Es importante tener en cuenta que hay límites en el análisis que puede realizar un compilador para identificar las instancias de la variante 1. Por lo tanto, no hay ninguna garantía de que todos los posibles casos de variante 1 se instrumentan bajo **/qspectre**.

### <a name="performance-impact"></a>Impacto de rendimiento

El impacto de rendimiento **/qspectre** se ha visto que ser insignificante en varias bases de código muy grandes, pero no hay ninguna garantía de que el rendimiento del código sometido a **/qspectre** no se ve afectada. Debe evaluar el código para determinar el efecto de la opción de rendimiento. Si sabe que no se requiere la mitigación en un bucle o bloque críticos de rendimiento, la mitigación puede deshabilitarse de forma selectiva mediante el uso de un [__declspec(spectre(nomitigation))](../../cpp/spectre.md) directiva. Esta directiva no está disponible en los compiladores que admiten solo el **/d2guardspecload** opción.

### <a name="required-libraries"></a>Bibliotecas necesarias

El **/qspectre** opción del compilador genera código que se vincule implícitamente las versiones de las bibliotecas en tiempo de ejecución que se han creado para proporcionar las mitigaciones de Spectre. Estas bibliotecas son componentes opcionales que deben instalarse mediante el instalador de Visual Studio:

- VC ++ 2017 versión *número_de_versión* Libs para Spectre (x86 y x64)
- ATL de Visual C++ (x86/x64) con mitigaciones de Spectre
- MFC de Visual C++ para x86/x64 con mitigaciones de Spectre

Si compila el código mediante el uso de **/qspectre** y estas bibliotecas no están instalados, los informes del sistema de compilación **advertencia MSB8038: mitigación de Spectre está habilitada pero no se encuentran las bibliotecas de Spectre mitigadas**. Si se produce un error en el código MFC o ATL generar y el vinculador informa de un error como **error irrecuperable LNK1104: no se puede abrir el archivo '/ oldnames.lib'**, estas bibliotecas que falta pueden ser la causa.

### <a name="additional-information"></a>Información adicional

Para obtener más información, consulte el sitio oficial [ADV180002 asesoramiento de seguridad de Microsoft, la orientación para mitigar las vulnerabilidades de canal lateral de ejecución especulativa](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Guía también está disponible de Intel, [especulativa mitigaciones de canal lateral de ejecución](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)y ARM, [canales del lado de caché especulación](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Para obtener información específica de Windows de las mitigaciones de Spectre y Meltdown, consulte [comprender el impacto de rendimiento de las mitigaciones de Spectre y Meltdown en sistemas Windows](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) en el blog de Microsoft Secure. Para obtener información general de vulnerabilidad de Spectre direccionada por las mitigaciones de MSVC, consulte [mitigaciones de Spectre en MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) en el blog del equipo de Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Escriba el **/qspectre** opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** para aplicar el cambio.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)  
[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
