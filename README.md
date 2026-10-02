# 👻 Módulo de Seguridade Ghost
**Ferramenta de Endurecemento de Seguridade Windows & Azure baseada en PowerShell**

> **Endurecemento proactivo de seguridade para puntos finais de Windows e contornos Azure.** Ghost proporciona funcións de endurecemento baseadas en PowerShell que poden axudar a reducir vectores de ataque comúns desactivando servizos e protocolos innecesarios.

## ⚠️ Importantes Descargos de Responsabilidade

**PROBAS REQUIRIDAS**: Probe sempre Ghost primeiro en contornos que non sexan de produción. A desactivación de servizos pode afectar funcións empresariais lexítimas.

**SEN GARANTÍAS**: Aínda que Ghost ten como obxectivo vectores de ataque comúns, ningunha ferramenta de seguridade pode previr todos os ataques. Este é un compoñente dunha estratexia de seguridade integral.

**IMPACTO OPERACIONAL**: Algunhas funcións poden afectar a funcionalidade do sistema. Revise cada configuración coidadosamente antes do despregue.

**AVALIACIÓN PROFESIONAL**: Para contornos de produción, consulte con profesionais de seguridade para asegurar que as configuracións se aliñen coas necesidades da súa organización.

## 📊 O Panorama de Seguridade

Os danos por ransomware alcanzaron **57 mil millóns de dólares en 2025**, e a investigación indica que moitos ataques exitosos explotan servizos básicos de Windows e configuracións incorrectas. Os vectores de ataque comúns inclúen:

- **90% dos incidentes de ransomware** involucran explotación RDP
- **Vulnerabilidades SMBv1** permitiron ataques como WannaCry e NotPetya
- **Macros de documentos** seguen sendo un método primario de entrega de malware
- **Ataques baseados en USB** continúan dirixíndose a redes illadas
- **Abuso de PowerShell** aumentou significativamente nos últimos anos

## 🛡️ Funcións de Seguridade Ghost

Ghost proporciona **16 funcións de endurecemento Windows** máis **integración de seguridade Azure**:

### Endurecemento de Punto Final Windows

| Función | Propósito | Consideracións |
|---------|-----------|----------------|
| `Set-RDP` | Xestiona o acceso a Escritorio Remoto | Pode afectar a administración remota |
| `Set-SMBv1` | Controla o protocolo SMB herdado | Requirido para sistemas moi antigos |
| `Set-AutoRun` | Controla AutoPlay/AutoRun | Pode afectar a comodidade do usuario |
| `Set-USBStorage` | Restrinxe dispositivos de almacenamento USB | Pode afectar o uso lexítimo de USB |
| `Set-Macros` | Controla a execución de macros de Office | Pode afectar documentos habilitados con macros |
| `Set-PSRemoting` | Xestiona PowerShell remoting | Pode afectar a xestión remota |
| `Set-WinRM` | Controla Windows Remote Management | Pode afectar a administración remota |
| `Set-LLMNR` | Xestiona o protocolo de resolución de nomes | Xeralmente seguro desactivar |
| `Set-NetBIOS` | Controla NetBIOS sobre TCP/IP | Pode afectar aplicacións herdadas |
| `Set-AdminShares` | Xestiona recursos compartidos administrativos | Pode afectar o acceso a ficheiros remotos |
| `Set-Telemetry` | Controla a recolla de datos | Pode afectar capacidades de diagnóstico |
| `Set-GuestAccount` | Xestiona a conta de Convidado | Xeralmente seguro desactivar |
| `Set-ICMP` | Controla respostas ping | Pode afectar diagnósticos de rede |
| `Set-RemoteAssistance` | Xestiona Asistencia Remota | Pode afectar operacións de helpdesk |
| `Set-NetworkDiscovery` | Controla descubrimento de rede | Pode afectar navegación de rede |
| `Set-Firewall` | Xestiona Firewall de Windows | Crítico para seguridade de rede |

### Seguridade de Nube Azure

| Función | Propósito | Requisitos |
|---------|-----------|------------|
| `Set-AzureSecurityDefaults` | Habilita seguridade básica de Azure AD | Permisos de Microsoft Graph |
| `Set-AzureConditionalAccess` | Configura políticas de acceso | Licenzas Azure AD P1/P2 |
| `Set-AzurePrivilegedUsers` | Audita contas privilexiadas | Permisos de Administrador Global |

### Opcións de Despregue Empresarial

| Método | Caso de Uso | Requisitos |
|--------|-------------|------------|
| **Execución Directa** | Probas, contornos pequenos | Dereitos de administrador local |
| **Group Policy** | Contornos de dominio | Administrador de dominio, xestión GP |
| **Microsoft Intune** | Dispositivos xestionados na nube | Licenzas Intune, Graph API |

## 🚀 Inicio Rápido

### Avaliación de Seguridade
```powershell
# Cargar módulo Ghost
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Comprobar postura de seguridade actual
Get-Ghost
```

### Endurecemento Básico (Probe Primeiro)
```powershell
# Endurecemento esencial - probe primeiro en contorno de laboratorio
Set-Ghost -SMBv1 -AutoRun -Macros

# Revisar cambios
Get-Ghost
```

### Despregue Empresarial
```powershell
# Despregue Group Policy (contornos de dominio)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Despregue Intune (dispositivos xestionados na nube)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Métodos de Instalación

### Opción 1: Descarga Directa (Probas)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### Opción 2: Instalación de Módulo
```powershell
# Instalar desde PowerShell Gallery (cando dispoñible)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Opción 3: Despregue Empresarial
```powershell
# Copiar a localización de rede para despregue Group Policy
# Configurar scripts PowerShell de Intune para despregue en nube
```

## 💼 Exemplos de Casos de Uso

### Pequena Empresa
```powershell
# Protección básica con impacto mínimo
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Contorno Sanitario
```powershell
# Endurecemento centrado en HIPAA
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Servizos Financeiros
```powershell
# Configuración de alta seguridade
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Organización Cloud-First
```powershell
# Despregue xestionado por Intune
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 📝 Detalles de Funcións

### Funcións de Endurecemento Principais

#### Servizos de Rede
- **RDP**: Bloquea acceso a escritorio remoto ou aleatoriza porto
- **SMBv1**: Desactiva protocolo de compartición de ficheiros herdado
- **ICMP**: Prevén respostas ping para recoñecemento
- **LLMNR/NetBIOS**: Bloquea protocolos de resolución de nomes herdados

#### Seguridade de Aplicacións
- **Macros**: Desactiva execución de macros en aplicacións Office
- **AutoRun**: Prevén execución automática desde medios extraíbles

#### Xestión Remota
- **PSRemoting**: Desactiva sesións remotas de PowerShell
- **WinRM**: Para Windows Remote Management
- **Asistencia Remota**: Bloquea conexións de asistencia remota

#### Control de Acceso
- **Recursos Compartidos Admin**: Desactiva recursos compartidos C$, ADMIN$
- **Conta de Convidado**: Desactiva acceso da conta de Convidado
- **Almacenamento USB**: Restrinxe uso de dispositivos USB

### Integración Azure
```powershell
# Conectar a inquilino Azure
Connect-AzureGhost -Interactive

# Habilitar valores predeterminados de seguridade
Set-AzureSecurityDefaults -Enable

# Configurar acceso condicional
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Auditar usuarios privilexiados
Set-AzurePrivilegedUsers -AuditOnly
```

### Integración Intune (Novo en v2)
```powershell
# Conectar a Intune
Connect-IntuneGhost -Interactive

# Despregar vía políticas Intune
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Consideracións Importantes

### Requisitos de Proba
- **Contorno de Laboratorio**: Probe todas as configuracións primeiro en contorno illado
- **Despregue Faseado**: Despregar gradualmente para identificar problemas
- **Plan de Volta Atrás**: Asegurar que pode reverter cambios se fose necesario
- **Documentación**: Rexistrar que configuracións funcionan para o seu contorno

### Impacto Potencial
- **Produtividade do Usuario**: Algunhas configuracións poden afectar fluxos de traballo diarios
- **Aplicacións Herdadas**: Sistemas máis antigos poden requirir certos protocolos
- **Acceso Remoto**: Considerar impacto na administración remota lexítima
- **Procesos Empresariais**: Verificar que as configuracións non rompen funcións críticas

### Limitacións de Seguridade
- **Defensa en Profundidade**: Ghost é unha capa de seguridade, non unha solución completa
- **Xestión Continua**: A seguridade require monitorización e actualizacións continuas
- **Formación de Usuario**: Os controis técnicos deben emparellarse con concienciación de seguridade
- **Evolución de Ameazas**: Os novos métodos de ataque poden eludir proteccións actuais

## 🎯 Exemplos de Escenarios de Ataque

Aínda que Ghost ten como obxectivo vectores de ataque comúns, a prevención específica depende da implementación e proba adecuadas:

### Ataques Estilo WannaCry
- **Mitigación**: `Set-Ghost -SMBv1` desactiva o protocolo vulnerable
- **Consideración**: Asegurar que ningún sistema herdado require SMBv1

### Ransomware Baseado en RDP
- **Mitigación**: `Set-Ghost -RDP` bloquea acceso a escritorio remoto
- **Consideración**: Pode requirir métodos alternativos de acceso remoto

### Malware Baseado en Documentos
- **Mitigación**: `Set-Ghost -Macros` desactiva execución de macros
- **Consideración**: Pode afectar documentos lexítimos habilitados con macros

### Ameazas Entregadas por USB
- **Mitigación**: `Set-Ghost -USBStorage -AutoRun` restrinxe funcionalidade USB
- **Consideración**: Pode afectar uso lexítimo de dispositivos USB

## 🏢 Características Empresariais

### Soporte Group Policy
```powershell
# Aplicar configuracións vía rexistro Group Policy
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# As configuracións aplícanse a nivel de dominio despois da actualización GP
gpupdate /force
```

### Integración Microsoft Intune
```powershell
# Crear políticas Intune para configuracións Ghost
Set-IntuneGhost -Settings $GhostSettings -Interactive

# As políticas desprégan automaticamente a dispositivos xestionados
```

### Informes de Cumprimento
```powershell
# Xerar informe de avaliación de seguridade
Get-Ghost | Export-Csv -Path "AuditoriaSeguridade-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Informe de postura de seguridade Azure
Get-AzureGhost | Out-File "InformeSegurideAzure.txt"
```

## 📚 Mellores Prácticas

### Pre-despregue
1. **Documentar Estado Actual**: Execute `Get-Ghost` antes dos cambios
2. **Probar Minuciosamente**: Validar en contorno de non-produción
3. **Planificar Volta Atrás**: Saber como reverter cada configuración
4. **Revisión de Interesados**: Asegurar que unidades empresariais aproven cambios

### Durante o Despregue
1. **Enfoque Faseado**: Despregar primeiro a grupos piloto
2. **Monitorizar Impacto**: Vixiar queixas de usuarios ou problemas do sistema
3. **Documentar Problemas**: Rexistrar calquera problema para referencia futura
4. **Comunicar Cambios**: Informar usuarios sobre melloras de seguridade

### Post-despregue
1. **Avaliación Regular**: Execute periodicamente `Get-Ghost` para verificar configuracións
2. **Actualizar Documentación**: Manter configuracións de seguridade actuais
3. **Revisar Efectividade**: Monitorizar para incidentes de seguridade
4. **Mellora Continua**: Axustar configuracións baseándose no panorama de ameazas

## 🔧 Resolución de Problemas

### Problemas Comúns
- **Erros de Permisos**: Asegurar sesión PowerShell elevada
- **Dependencias de Servizo**: Algúns servizos poden ter dependencias
- **Compatibilidade de Aplicacións**: Probar con aplicacións empresariais
- **Conectividade de Rede**: Verificar que acceso remoto siga funcionando

### Opcións de Recuperación
```powershell
# Reactivar servizos específicos se fose necesario
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Sobre o Autor

**Jim Tyler** - Microsoft MVP para PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10.000+ subscritores)
- **Boletín**: [PowerShell.News](https://powershell.news) - Intelixencia de seguridade semanal
- **Autor**: "PowerShell for Systems Engineers"
- **Experiencia**: Décadas de automatización PowerShell e seguridade Windows

## 📄 Licenza & Descargo de Responsabilidade

### Licenza MIT
Ghost fornécese baixo a Licenza MIT para uso, modificación e distribución libres.

### Descargo de Responsabilidade de Seguridade
- **Sen Garantía**: Ghost fornécese "tal como está" sen garantía de ningún tipo
- **Probas Requiridas**: Probe sempre primeiro en contornos de non-produción
- **Guía Profesional**: Consulte profesionais de seguridade para despregues de produción
- **Impacto Operacional**: Os autores non son responsables de calquera interrupción operacional
- **Seguridade Integral**: Ghost é un compoñente dunha estratexia de seguridade completa

### Soporte
- **GitHub Issues**: [Informar bugs ou solicitar características](https://github.com/jimrtyler/Ghost/issues)
- **Documentación**: Use `Get-Help <función> -Full` para axuda detallada
- **Comunidade**: Foros da comunidade PowerShell e seguridade

---

**🔒 Fortalecer a súa postura de seguridade con Ghost - pero probe sempre primeiro.**

```powershell
# Comezar con avaliación, non suposicións
Get-Ghost
```

**⭐ Dar unha estrela a este repositorio se Ghost axuda a mellorar a súa postura de seguridade!**