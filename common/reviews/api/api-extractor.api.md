## API Report File for "@microsoft/api-extractor"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import { INodePackageJson } from '@microsoft/node-core-library';
import { JsonSchema } from '@microsoft/node-core-library';
import * as ts from 'typescript';
import * as tsdoc from '@microsoft/tsdoc';

// @public
export class CompilerState {
    static create(extractorConfig: ExtractorConfig, options?: ICompilerStateCreateOptions): CompilerState;
    readonly program: ts.Program;
    }

// @public
export const enum ConsoleMessageId {
    ApiReportCopied = "console-api-report-copied",
    ApiReportCreated = "console-api-report-created",
    ApiReportFolderMissing = "console-api-report-folder-missing",
    ApiReportNotCopied = "console-api-report-not-copied",
    ApiReportUnchanged = "console-api-report-unchanged",
    FoundTSDocMetadata = "console-found-tsdoc-metadata",
    WritingDocModelFile = "console-writing-doc-model-file",
    WritingDtsRollup = "console-writing-dts-rollup"
}

// @public
export class Extractor {
    static invoke(extractorConfig: ExtractorConfig, options?: IExtractorInvokeOptions): ExtractorResult;
    static loadConfigAndInvoke(configFilePath: string, options?: IExtractorInvokeOptions): ExtractorResult;
    static readonly packageName: string;
    static readonly version: string;
}

// @public
export class ExtractorConfig {
    readonly apiJsonFilePath: string;
    readonly apiReportEnabled: boolean;
    readonly betaTrimmedFilePath: string;
    readonly docModelEnabled: boolean;
    static readonly FILENAME: string;
    // @internal
    _getShortFilePath(absolutePath: string): string;
    static hasDtsFileExtension(filePath: string): boolean;
    static readonly jsonSchema: JsonSchema;
    static loadFile(jsonFilePath: string): IConfigFile;
    static loadFileAndPrepare(configJsonFilePath: string): ExtractorConfig;
    readonly mainEntryPointFilePath: string;
    readonly messages: IExtractorMessagesConfig;
    readonly omitTrimmingComments: boolean;
    readonly overrideTsconfig: {} | undefined;
    readonly packageFolder: string | undefined;
    readonly packageJson: INodePackageJson | undefined;
    static prepare(options: IExtractorConfigPrepareOptions): ExtractorConfig;
    readonly projectFolder: string;
    readonly publicTrimmedFilePath: string;
    readonly reportFilePath: string;
    readonly reportTempFilePath: string;
    readonly rollupEnabled: boolean;
    readonly skipLibCheck: boolean;
    readonly testMode: boolean;
    readonly tsconfigFilePath: string;
    readonly tsdocMetadataEnabled: boolean;
    readonly tsdocMetadataFilePath: string;
    readonly untrimmedFilePath: string;
}

// @public
export const enum ExtractorLogLevel {
    Error = "error",
    Info = "info",
    None = "none",
    Verbose = "verbose",
    Warning = "warning"
}

// @public
export class ExtractorMessage {
    // Warning: (ae-forgotten-export) The symbol "IExtractorMessageOptions" needs to be exported by the entry point index.d.ts
    // 
    // @internal
    constructor(options: IExtractorMessageOptions);
    readonly category: ExtractorMessageCategory;
    formatMessageWithLocation(workingPackageFolderPath: string): string;
    // (undocumented)
    formatMessageWithoutLocation(): string;
    handled: boolean;
    logLevel: ExtractorLogLevel;
    readonly messageId: tsdoc.TSDocMessageId | ExtractorMessageId | ConsoleMessageId | string;
    readonly properties: IExtractorMessageProperties;
    readonly sourceFileColumn: number | undefined;
    readonly sourceFileLine: number | undefined;
    readonly sourceFilePath: string | undefined;
    readonly text: string;
}

// @public
export const enum ExtractorMessageCategory {
    Compiler = "Compiler",
    Console = "console",
    Extractor = "Extractor",
    TSDoc = "TSDoc"
}

// @public
export const enum ExtractorMessageId {
    CyclicInheritDoc = "ae-cyclic-inherit-doc",
    DifferentReleaseTags = "ae-different-release-tags",
    ExtraReleaseTag = "ae-extra-release-tag",
    ForgottenExport = "ae-forgotten-export",
    IncompatibleReleaseTags = "ae-incompatible-release-tags",
    InternalMissingUnderscore = "ae-internal-missing-underscore",
    MisplacedPackageTag = "ae-misplaced-package-tag",
    MissingReleaseTag = "ae-missing-release-tag",
    PreapprovedBadReleaseTag = "ae-preapproved-bad-release-tag",
    PreapprovedUnsupportedType = "ae-preapproved-unsupported-type",
    UnresolvedInheritDocBase = "ae-unresolved-inheritdoc-base",
    UnresolvedInheritDocReference = "ae-unresolved-inheritdoc-reference",
    UnresolvedLink = "ae-unresolved-link"
}

// @public
export class ExtractorResult {
    // @internal
    constructor(properties: ExtractorResult);
    readonly apiReportChanged: boolean;
    readonly compilerState: CompilerState;
    readonly errorCount: number;
    readonly extractorConfig: ExtractorConfig;
    readonly succeeded: boolean;
    readonly warningCount: number;
}

// @public
export interface ICompilerStateCreateOptions {
    additionalEntryPoints?: string[];
    typescriptCompilerFolder?: string;
}

// @public
export interface IConfigApiReport {
    enabled: boolean;
    reportFileName?: string;
    reportFolder?: string;
    reportTempFolder?: string;
}

// @public
export interface IConfigCompiler {
    overrideTsconfig?: {};
    skipLibCheck?: boolean;
    tsconfigFilePath?: string;
}

// @public
export interface IConfigDocModel {
    apiJsonFilePath?: string;
    enabled: boolean;
}

// @public
export interface IConfigDtsRollup {
    betaTrimmedFilePath?: string;
    enabled: boolean;
    omitTrimmingComments?: boolean;
    publicTrimmedFilePath?: string;
    untrimmedFilePath?: string;
}

// @public
export interface IConfigFile {
    apiReport?: IConfigApiReport;
    compiler?: IConfigCompiler;
    docModel?: IConfigDocModel;
    // @beta
    dtsRollup?: IConfigDtsRollup;
    extends?: string;
    mainEntryPointFilePath: string;
    messages?: IExtractorMessagesConfig;
    projectFolder?: string;
    testMode?: boolean;
    // @beta
    tsdocMetadata?: IConfigTsdocMetadata;
}

// @public
export interface IConfigMessageReportingRule {
    addToApiReportFile?: boolean;
    logLevel: ExtractorLogLevel;
}

// @public
export interface IConfigMessageReportingTable {
    [messageId: string]: IConfigMessageReportingRule;
}

// @public
export interface IConfigTsdocMetadata {
    enabled: boolean;
    tsdocMetadataFilePath?: string;
}

// @public
export interface IExtractorConfigPrepareOptions {
    configObject: IConfigFile;
    configObjectFullPath: string | undefined;
    packageJson?: INodePackageJson | undefined;
    packageJsonFullPath: string | undefined;
}

// @public
export interface IExtractorInvokeOptions {
    compilerState?: CompilerState;
    localBuild?: boolean;
    messageCallback?: (message: ExtractorMessage) => void;
    showVerboseMessages?: boolean;
    typescriptCompilerFolder?: string;
}

// @public
export interface IExtractorMessageProperties {
    readonly exportName?: string;
}

// @public
export interface IExtractorMessagesConfig {
    compilerMessageReporting?: IConfigMessageReportingTable;
    extractorMessageReporting?: IConfigMessageReportingTable;
    tsdocMessageReporting?: IConfigMessageReportingTable;
}


```