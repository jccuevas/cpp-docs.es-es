---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e0d3af50015b77af297cbee22f439cd17d803de9
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344162"
---
# <a name="qspectre"></a>/Qspectre

Especifica la generación de instrucciones del compilador para mitigar determinadas vulnerabilidades de seguridad de la variante 1 de Spectre.

## <a name="syntax"></a>Sintaxis

> **/Qspectre**

## <a name="remarks"></a>Comentarios

La opción **/Qspectre** está disponible en la versión 15.5.5 de Visual Studio 2017 y versiones posteriores, y en Visual Studio 2015 Update 3 a través de [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Hace que el compilador inserte instrucciones para mitigar determinadas [vulnerabilidades de seguridad de Spectre](https://spectreattack.com/spectre.pdf). Se llama a estas vulnerabilidades *ataques de canal lateral de ejecución especulativa*. Afectan a muchos sistemas operativos y los procesadores modernos, incluidos procesadores de Intel, AMD y ARM.

La opción **/Qspectre** está desactivada de forma predeterminada.

En su versión inicial, la opción **/Qspectre** solo funcionaba en código optimizado. En Visual Studio 2017 versión 15.7 y posteriores, la opción **/Qspectre** se admite en todos los niveles de optimización.

También hay versiones con mitigación de Spectre de bibliotecas de Microsoft Visual C++. Las bibliotecas de Spectre mitigadas para Visual Studio 2017 y versiones posteriores se pueden descargar en el instalador de Visual Studio. Se encuentran en el **componentes individuales** pestaña **compiladores, herramientas de compilación y tiempos de ejecución**, y que tienen "Bibliotecas de Spectre" en el nombre. Hay bibliotecas de tiempo de ejecución estáticas y DLL con mitigación habilitada disponibles para un subconjunto de los runtimes de Visual C++: código de inicio de VC++, vcruntime140, msvcp140, concrt140 y vcamp140. Implementación de la aplicación local solo son compatibles con los archivos DLL. El contenido del objeto Visual C++ 2017 y versiones posteriores en tiempo de ejecución bibliotecas redistribuibles no se han modificado.

También puede instalar las bibliotecas de Spectre mitigadas de MFC y ATL. Se encuentran en el **componentes individuales** pestaña **SDK, bibliotecas y marcos**.

### <a name="applicability"></a>Aplicabilidad

Si el código funciona en los datos que se cruza un límite de confianza, se recomienda que utilice el **/qspectre** opción recompilar y reimplementar el código para mitigar este problema tan pronto como sea posible. Un ejemplo de dicho código es código que carga la entrada de confianza que puede afectar a la ejecución. Por ejemplo, código que realice el procedimiento remoto llama, analiza la entrada no confiable o archivos o utiliza otras interfaces de comunicación local entre procesos (IPC). Es posible que las técnicas estándar de espacio aislado no sean suficientes. Investigue los espacios aislados cuidadosamente antes de decidir que el código no cruce un límite de confianza.

### <a name="availability"></a>Disponibilidad

El **/qspectre** opción está disponible en versión 15.5.5 de Visual Studio 2017 y en todas las actualizaciones de Microsoft C++ compiladores (MSVC) realizados en o después del 23 de enero de 2018. Use el instalador de Visual Studio para actualizar el compilador y para instalar las bibliotecas de Spectre mitigadas como componentes individuales. La opción **/Qspectre** también está disponible en Visual Studio 2015 Update 3 a través de una revisión. Para más información, vea [KB 4338871](https://support.microsoft.com/help/4338871).

Todas las versiones de Visual Studio 2017 versión 15.5 y todas las versiones preliminares de Visual Studio 2017 versión 15.6. incluir una opción sin documentar, **/d2guardspecload**. Equivale al comportamiento inicial de **/qspectre**. Puede usar **/d2guardspecload** para aplicar la mismas mitigaciones al código en estas versiones del compilador. Se recomienda actualizar la compilación para usar **/qspectre** en los compiladores que admiten la opción. El **/qspectre** opción también puede admitir las mitigaciones de nuevo en versiones posteriores del compilador.

### <a name="effect"></a>Efecto

La opción **/Qspectre** genera código para mitigar la variante 1 de Spectre, Derivación de comprobación de límites, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Funciona mediante la inserción de instrucciones que actúan como una barrera de ejecución de código especulativo. Las instrucciones específicas que se usan para mitigar la especulación de procesador dependen del procesador y su microarquitectura, y pueden cambiar en versiones futuras del compilador.

Cuando se habilita la **/qspectre** opción, el compilador intenta identificar instancias donde la ejecución especulativa puede omitir las comprobaciones de límites. Es donde inserta las instrucciones de barrera. Es importante tener en cuenta los límites para el análisis que puede hacer un compilador para identificar las instancias de variante 1. Por lo tanto, no hay ninguna garantía de que todos los posibles casos de variante 1 se instrumentan bajo **/qspectre**.

### <a name="performance-impact"></a>Impacto del rendimiento

El impacto de rendimiento **/qspectre** parecía ser insignificante en varias bases de código considerable. Sin embargo, no hay garantías de que el rendimiento del código sometido a **/qspectre** no se ve afectada. Debe realizar pruebas comparativas del código para determinar el efecto de la opción en el rendimiento. Si sabe que la mitigación no es necesario en un bucle o bloque de rendimiento crítico, puede deshabilitar selectivamente la mitigación mediante el uso de un [__declspec(spectre(nomitigation))](../../cpp/spectre.md) directiva. Esta directiva no está disponible en los compiladores que admiten solo el **/d2guardspecload** opción.

### <a name="required-libraries"></a>Bibliotecas necesarias

El **/qspectre** opción del compilador genera código que se vincule implícitamente las versiones de las bibliotecas en tiempo de ejecución compiladas para proporcionar las mitigaciones de Spectre. Estas bibliotecas son componentes opcionales que se deben instalar mediante el instalador de Visual Studio:

- Versión de MSVC *números_de_versión* Bibliotecas para Spectre \[(x86 y x64) | (ARM) | (ARM64)]
- ATL de Visual C++ para \[(x86/x64) | ARM | ARM64] con mitigaciones de Spectre
- MFC de Visual C++ para \[(x86/x64) | ARM | ARM64] con mitigaciones de Spectre

Si compila el código mediante el uso de **/qspectre** y estas bibliotecas no están instalados, los informes del sistema de compilación **advertencia MSB8038: La mitigación de Spectre está habilitada pero no se han encontrado bibliotecas de Spectre mitigadas**. Si se produce un error en el código MFC o ATL compilar, y el vinculador informa de un error como **error irrecuperable LNK1104: no se puede abrir el archivo '/ oldnames.lib'** , estas bibliotecas que falta pueden ser la causa.

### <a name="additional-information"></a>Información adicional

Para obtener más información, consulte el sitio oficial [ADV180002 asesoramiento de seguridad de Microsoft, la orientación para mitigar las vulnerabilidades de canal lateral de ejecución especulativa](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). También hay instrucciones de Intel, [Speculative Execution Side Channel Mitigations](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) (Mitigaciones de canal lateral de ejecución especulativa) y ARM, [Cache Speculation Side-channels](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) (Almacenamiento en caché de canales de ejecución especulativa). Para obtener información específica de Windows de las mitigaciones de Spectre y Meltdown, consulte [comprender el impacto de rendimiento de las mitigaciones de Spectre y Meltdown en sistemas Windows](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/). Para obtener información general de las vulnerabilidades de Spectre que abordan las mitigaciones de MSVC, consulte [mitigaciones de Spectre en MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) en el C++ blog del equipo.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C /C++**  > **Línea de comandos**.

1. Escriba la opción del compilador **/Qspectre** en el cuadro **Opciones adicionales**. Seleccione **Aceptar** para aplicar el cambio.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](q-options-low-level-operations.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
