---
title: /Qspectre
ms.date: 09/06/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.SpectreMitigation
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e8d03075a980a9b9c345ce351413e39a3c3444cb
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808833"
---
# <a name="qspectre"></a>/Qspectre

Especifica la generación de instrucciones del compilador para mitigar determinadas vulnerabilidades de seguridad de la variante 1 de Spectre.

## <a name="syntax"></a>Sintaxis

> **/Qspectre**

## <a name="remarks"></a>Comentarios

La opción **/Qspectre** está disponible en la versión 15.5.5 de Visual Studio 2017 y versiones posteriores, y en Visual Studio 2015 Update 3 a través de [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Hace que el compilador inserte instrucciones para mitigar determinadas [vulnerabilidades de seguridad de Spectre](https://spectreattack.com/spectre.pdf). Estas vulnerabilidades se denominan *ataques de canal lateral de ejecución especulativa*. Afectan a muchos sistemas operativos y procesadores modernos, incluidos procesadores de Intel, AMD y ARM.

La opción **/Qspectre** está desactivada de forma predeterminada.

En su versión inicial, la opción **/Qspectre** solo funcionaba en código optimizado. En Visual Studio 2017 versión 15.7 y posteriores, la opción **/Qspectre** se admite en todos los niveles de optimización.

También hay versiones con mitigación de Spectre de bibliotecas de Microsoft Visual C++. Las bibliotecas de Spectre mitigadas para Visual Studio 2017 y versiones posteriores se pueden descargar en el instalador de Visual Studio. Se encuentran en la pestaña **componentes individuales** en **compiladores, herramientas de compilación y tiempos de ejecución**, y tienen "bibliotecas para Spectre" en el nombre. Hay bibliotecas de tiempo de ejecución estáticas y DLL con mitigación habilitada disponibles para un subconjunto de los runtimes de Visual C++: código de inicio de VC++, vcruntime140, msvcp140, concrt140 y vcamp140. Los archivos dll solo se admiten para la implementación local de la aplicación. No se ha modificado el C++ contenido del paquete redistribuible de las bibliotecas en tiempo de ejecución de Visual 2017 y posteriores.

También puede instalar bibliotecas mitigadas por Spectre para MFC y ATL. Se encuentran en la pestaña **componentes individuales** en **SDK, bibliotecas y marcos**.

> [!NOTE]
> No hay ninguna versión de las bibliotecas mitigadas por Spectre para las aplicaciones o componentes de Windows universal (UWP). No es posible la implementación local de aplicaciones de estas bibliotecas.

### <a name="applicability"></a>Aplicabilidad

Si el código funciona en datos que atraviesan un límite de confianza, se recomienda usar la opción **/Qspectre** para volver a generar y volver a implementar el código para mitigar este problema lo antes posible. Un ejemplo de este tipo de código es el código que carga la entrada que no es de confianza y que puede afectar a la ejecución. Por ejemplo, el código que realiza llamadas a procedimientos remotos, analiza los archivos o la entrada que no son de confianza, o utiliza otras interfaces de comunicación entre procesos (IPC) locales. Es posible que las técnicas estándar de espacio aislado no sean suficientes. Investigue detenidamente los espacios aislados antes de decidir si el código no cruza un límite de confianza.

### <a name="availability"></a>Disponibilidad

La opción **/Qspectre** está disponible en la versión 15.5.5 de Visual Studio 2017 y en todas las actualizaciones C++ de los compiladores de Microsoft (MSVC) realizadas a partir del 23 de enero de 2018. Use el instalador de Visual Studio para actualizar el compilador y para instalar las bibliotecas de Spectre mitigadas como componentes individuales. La opción **/Qspectre** también está disponible en Visual Studio 2015 Update 3 a través de una revisión. Para más información, vea [KB 4338871](https://support.microsoft.com/help/4338871).

Todas las versiones de Visual Studio 2017 versión 15,5 y todas las vistas previas de Visual Studio 2017 versión 15,6. incluya una opción no documentada, **/d2guardspecload**. Es equivalente al comportamiento inicial de **/Qspectre**. Puede usar **/d2guardspecload** para aplicar la mismas mitigaciones al código en estas versiones del compilador. Se recomienda actualizar la compilación para usar **/Qspectre** en los compiladores que admiten la opción. La opción **/Qspectre** también puede admitir nuevas mitigaciones en versiones posteriores del compilador.

### <a name="effect"></a>Efecto

La opción **/Qspectre** genera código para mitigar la variante 1 de Spectre, Derivación de comprobación de límites, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Funciona mediante la inserción de instrucciones que actúan como una barrera de ejecución de código especulativo. Las instrucciones específicas que se usan para mitigar la especulación de procesador dependen del procesador y su microarquitectura, y pueden cambiar en versiones futuras del compilador.

Cuando se habilita la opción **/Qspectre** , el compilador intenta identificar las instancias en las que la ejecución especulativa puede omitir las comprobaciones de los límites. Aquí es donde inserta las instrucciones de barrera. Es importante tener en cuenta los límites del análisis que puede realizar un compilador para identificar las instancias de la variante 1. Como tal, no hay ninguna garantía de que todas las instancias posibles de la variante 1 se instrumentan en **/Qspectre**.

### <a name="performance-impact"></a>Impacto en el rendimiento

El impacto en el rendimiento de **/Qspectre** parecía ser insignificante en varias bases de código de gran tamaño. Sin embargo, no hay ninguna garantía de que el rendimiento del código en **/Qspectre** permanezca inalterado. Debe realizar pruebas comparativas del código para determinar el efecto de la opción en el rendimiento. Si sabe que la mitigación no es necesaria en un bloque o un bucle crítico para el rendimiento, puede deshabilitar selectivamente la mitigación mediante el uso de una directiva [_ _ declspec (Spectre (nomitigation))](../../cpp/spectre.md) . Esta Directiva no está disponible en los compiladores que solo admiten la opción **/d2guardspecload** .

### <a name="required-libraries"></a>Bibliotecas necesarias

La opción del compilador **/Qspectre** genera código que vincula implícitamente las versiones de las bibliotecas en tiempo de ejecución compiladas para proporcionar mitigaciones de Spectre. Estas bibliotecas son componentes opcionales que se deben instalar mediante el instalador de Visual Studio:

- Versión de MSVC *números_de_versión* Bibliotecas para Spectre \[(x86 y x64) | (ARM) | (ARM64)]
- ATL de Visual C++ para \[(x86/x64) | ARM | ARM64] con mitigaciones de Spectre
- MFC de Visual C++ para \[(x86/x64) | ARM | ARM64] con mitigaciones de Spectre

Si compila el código mediante **/Qspectre** y estas bibliotecas no están instaladas, el sistema de compilación **notifica MSB8038 de ADVERTENCIA: La mitigación de Spectre está habilitada pero no se han encontrado bibliotecas de Spectre mitigadas**. Si el código MFC o ATL no se puede compilar y el vinculador informa de un error como **error IRRECUPERABLE LNK1104: no se puede abrir el archivo '/OLDNAMES.lib. lib '** , puede que estas bibliotecas que faltan sean la causa.

### <a name="additional-information"></a>Información adicional

Para obtener más información, consulte el [asesoramiento oficial de seguridad de Microsoft ADV180002, guía para mitigar las vulnerabilidades de canal lateral de ejecución especulativa](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). También hay instrucciones de Intel, [Speculative Execution Side Channel Mitigations](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) (Mitigaciones de canal lateral de ejecución especulativa) y ARM, [Cache Speculation Side-channels](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) (Almacenamiento en caché de canales de ejecución especulativa). Para obtener información general específica de Windows sobre las mitigaciones de Spectre y Meltdown, consulte [Descripción del impacto en el rendimiento de las mitigaciones de Spectre y Meltdown en los sistemas Windows](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/). Para obtener información general sobre las vulnerabilidades de Spectre dirigidas por las mitigaciones de MSVC, consulte [mitigaciones de Spectre en MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) en el blog del C++ equipo.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

::: moniker range="vs-2019"

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **propiedades** > de > configuración **C/C++**  **generación de código** .

1. Seleccione un nuevo valor para la propiedad de **mitigación Spectre** . Seleccione **Aceptar** para aplicar el cambio.

::: moniker-end

::: moniker range="<=vs-2017"

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de **propiedades propiedades** > de > configuración **CC++ /** **línea de comandos** .

1. Escriba la opción del compilador **/Qspectre** en el cuadro **Opciones adicionales**. Seleccione **Aceptar** para aplicar el cambio.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](q-options-low-level-operations.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
