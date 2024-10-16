## API Report File for "@backstage/plugin-kubernetes-backend"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
import { AuthenticationStrategy as AuthenticationStrategy_2 } from '@backstage/plugin-kubernetes-node';
import { AuthMetadata as AuthMetadata_2 } from '@backstage/plugin-kubernetes-node';
import { AuthService } from '@backstage/backend-plugin-api';
import { BackendFeature } from '@backstage/backend-plugin-api';
import { BackstageCredentials } from '@backstage/backend-plugin-api';
import { CatalogApi } from '@backstage/catalog-client';
import { ClusterDetails as ClusterDetails_2 } from '@backstage/plugin-kubernetes-node';
import { Config } from '@backstage/config';
import { CustomResource as CustomResource_2 } from '@backstage/plugin-kubernetes-node';
import { DiscoveryService } from '@backstage/backend-plugin-api';
import { Duration } from 'luxon';
import express from 'express';
import { HttpAuthService } from '@backstage/backend-plugin-api';
import * as k8sAuthTypes from '@backstage/plugin-kubernetes-node';
import { KubernetesClustersSupplier as KubernetesClustersSupplier_2 } from '@backstage/plugin-kubernetes-node';
import { KubernetesCredential as KubernetesCredential_2 } from '@backstage/plugin-kubernetes-node';
import { KubernetesFetcher as KubernetesFetcher_2 } from '@backstage/plugin-kubernetes-node';
import { KubernetesObjectsProvider as KubernetesObjectsProvider_2 } from '@backstage/plugin-kubernetes-node';
import { KubernetesRequestAuth } from '@backstage/plugin-kubernetes-common';
import type { KubernetesRequestBody } from '@backstage/plugin-kubernetes-common';
import { KubernetesServiceLocator as KubernetesServiceLocator_2 } from '@backstage/plugin-kubernetes-node';
import { Logger } from 'winston';
import { LoggerService } from '@backstage/backend-plugin-api';
import { ObjectToFetch as ObjectToFetch_2 } from '@backstage/plugin-kubernetes-node';
import { PermissionEvaluator } from '@backstage/plugin-permission-common';
import { PermissionsService } from '@backstage/backend-plugin-api';
import { RequestHandler } from 'http-proxy-middleware';
import { RootConfigService } from '@backstage/backend-plugin-api';
import { TokenCredential } from '@azure/identity';

// @public (undocumented)
export class AksStrategy implements AuthenticationStrategy_2 {
  // (undocumented)
  getCredential(
    _: ClusterDetails_2,
    requestAuth: KubernetesRequestAuth,
  ): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(): Error[];
}

// @public (undocumented)
export class AnonymousStrategy implements AuthenticationStrategy_2 {
  // (undocumented)
  getCredential(): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(): Error[];
}

// @public @deprecated (undocumented)
export type AuthenticationStrategy = k8sAuthTypes.AuthenticationStrategy;

// @public @deprecated (undocumented)
export type AuthMetadata = k8sAuthTypes.AuthMetadata;

// @public (undocumented)
export class AwsIamStrategy implements AuthenticationStrategy_2 {
  constructor(opts: { config: Config });
  // (undocumented)
  getCredential(
    clusterDetails: ClusterDetails_2,
  ): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(): Error[];
}

// @public (undocumented)
export class AzureIdentityStrategy implements AuthenticationStrategy_2 {
  constructor(logger: LoggerService, tokenCredential?: TokenCredential);
  // (undocumented)
  getCredential(): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(): Error[];
}

// @public @deprecated (undocumented)
export type ClusterDetails = k8sAuthTypes.ClusterDetails;

// @public @deprecated
export function createRouter(options: RouterOptions): Promise<express.Router>;

// @public @deprecated (undocumented)
export type CustomResource = k8sAuthTypes.CustomResource;

// @public @deprecated (undocumented)
export type CustomResourcesByEntity = k8sAuthTypes.CustomResourcesByEntity;

// @public (undocumented)
export const DEFAULT_OBJECTS: ObjectToFetch[];

// @public
export class DispatchStrategy implements AuthenticationStrategy_2 {
  constructor(options: DispatchStrategyOptions);
  // (undocumented)
  getCredential(
    clusterDetails: ClusterDetails_2,
    auth: KubernetesRequestAuth,
  ): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(authMetadata: AuthMetadata_2): Error[];
}

// @public (undocumented)
export type DispatchStrategyOptions = {
  authStrategyMap: {
    [key: string]: AuthenticationStrategy_2;
  };
};

// @public @deprecated (undocumented)
export type FetchResponseWrapper = k8sAuthTypes.FetchResponseWrapper;

// @public (undocumented)
export class GoogleServiceAccountStrategy implements AuthenticationStrategy_2 {
  // (undocumented)
  getCredential(): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(): Error[];
}

// @public (undocumented)
export class GoogleStrategy implements AuthenticationStrategy_2 {
  // (undocumented)
  getCredential(
    _: ClusterDetails_2,
    requestAuth: KubernetesRequestAuth,
  ): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(): Error[];
}

// @public
export const HEADER_KUBERNETES_AUTH: string;

// @public
export const HEADER_KUBERNETES_CLUSTER: string;

// @public @deprecated (undocumented)
export class KubernetesBuilder {
  constructor(env: KubernetesEnvironment);
  // (undocumented)
  addAuthStrategy(key: string, strategy: AuthenticationStrategy_2): this;
  // (undocumented)
  build(): KubernetesBuilderReturn;
  // (undocumented)
  protected buildAuthStrategyMap(): {
    [key: string]: AuthenticationStrategy_2;
  };
  // (undocumented)
  protected buildCatalogRelationServiceLocator(
    clusterSupplier: KubernetesClustersSupplier_2,
  ): KubernetesServiceLocator_2;
  // (undocumented)
  protected buildClusterSupplier(
    refreshInterval: Duration,
  ): KubernetesClustersSupplier_2;
  // (undocumented)
  protected buildCustomResources(): CustomResource_2[];
  // (undocumented)
  protected buildFetcher(): KubernetesFetcher_2;
  // (undocumented)
  protected buildHttpServiceLocator(
    _clusterSupplier: KubernetesClustersSupplier_2,
  ): KubernetesServiceLocator_2;
  // (undocumented)
  protected buildMultiTenantServiceLocator(
    clusterSupplier: KubernetesClustersSupplier_2,
  ): KubernetesServiceLocator_2;
  // (undocumented)
  protected buildObjectsProvider(
    options: KubernetesObjectsProviderOptions,
  ): KubernetesObjectsProvider_2;
  // (undocumented)
  protected buildProxy(
    logger: LoggerService,
    clusterSupplier: KubernetesClustersSupplier_2,
    discovery: DiscoveryService,
    httpAuth: HttpAuthService,
  ): KubernetesProxy;
  // (undocumented)
  protected buildRouter(
    objectsProvider: KubernetesObjectsProvider_2,
    clusterSupplier: KubernetesClustersSupplier_2,
    catalogApi: CatalogApi,
    proxy: KubernetesProxy,
    permissionApi: PermissionEvaluator,
    authService: AuthService,
    httpAuth: HttpAuthService,
  ): express.Router;
  // (undocumented)
  protected buildServiceLocator(
    method: ServiceLocatorMethod,
    clusterSupplier: KubernetesClustersSupplier_2,
  ): KubernetesServiceLocator_2;
  // (undocumented)
  protected buildSingleTenantServiceLocator(
    clusterSupplier: KubernetesClustersSupplier_2,
  ): KubernetesServiceLocator_2;
  // (undocumented)
  static createBuilder(env: KubernetesEnvironment): KubernetesBuilder;
  // (undocumented)
  protected readonly env: KubernetesEnvironment;
  // (undocumented)
  protected fetchClusterDetails(
    clusterSupplier: KubernetesClustersSupplier_2,
    options: {
      credentials: BackstageCredentials;
    },
  ): Promise<ClusterDetails_2[]>;
  // (undocumented)
  protected getAuthStrategyMap(): {
    [key: string]: AuthenticationStrategy_2;
  };
  // (undocumented)
  protected getClusterSupplier(): KubernetesClustersSupplier_2;
  // (undocumented)
  protected getFetcher(): KubernetesFetcher_2;
  // (undocumented)
  protected getObjectsProvider(
    options: KubernetesObjectsProviderOptions,
  ): KubernetesObjectsProvider_2;
  // (undocumented)
  protected getObjectTypesToFetch(): ObjectToFetch_2[] | undefined;
  // (undocumented)
  protected getProxy(
    logger: LoggerService,
    clusterSupplier: KubernetesClustersSupplier_2,
    discovery: DiscoveryService,
    httpAuth: HttpAuthService,
  ): KubernetesProxy;
  // (undocumented)
  protected getServiceLocator(): KubernetesServiceLocator_2;
  // (undocumented)
  protected getServiceLocatorMethod(): ServiceLocatorMethod;
  // (undocumented)
  setAuthStrategyMap(authStrategyMap: {
    [key: string]: AuthenticationStrategy_2;
  }): void;
  // (undocumented)
  setClusterSupplier(clusterSupplier?: KubernetesClustersSupplier_2): this;
  // (undocumented)
  setDefaultClusterRefreshInterval(refreshInterval: Duration): this;
  // (undocumented)
  setFetcher(fetcher?: KubernetesFetcher_2): this;
  // (undocumented)
  setObjectsProvider(objectsProvider?: KubernetesObjectsProvider_2): this;
  // (undocumented)
  setProxy(proxy?: KubernetesProxy): this;
  // (undocumented)
  setServiceLocator(serviceLocator?: KubernetesServiceLocator_2): this;
}

// @public @deprecated
export type KubernetesBuilderReturn = Promise<{
  router: express.Router;
  clusterSupplier: KubernetesClustersSupplier_2;
  customResources: CustomResource_2[];
  fetcher: KubernetesFetcher_2;
  proxy: KubernetesProxy;
  objectsProvider: KubernetesObjectsProvider_2;
  serviceLocator: KubernetesServiceLocator_2;
  authStrategyMap: {
    [key: string]: AuthenticationStrategy_2;
  };
}>;

// @public @deprecated (undocumented)
export type KubernetesClustersSupplier =
  k8sAuthTypes.KubernetesClustersSupplier;

// @public @deprecated (undocumented)
export type KubernetesCredential = k8sAuthTypes.KubernetesCredential;

// @public @deprecated (undocumented)
export interface KubernetesEnvironment {
  // (undocumented)
  auth?: AuthService;
  // (undocumented)
  catalogApi: CatalogApi;
  // (undocumented)
  config: Config;
  // (undocumented)
  discovery: DiscoveryService;
  // (undocumented)
  httpAuth?: HttpAuthService;
  // (undocumented)
  logger: LoggerService;
  // (undocumented)
  permissions: PermissionEvaluator;
}

// @public @deprecated (undocumented)
export type KubernetesFetcher = k8sAuthTypes.KubernetesFetcher;

// @public @deprecated (undocumented)
export type KubernetesObjectsProvider = k8sAuthTypes.KubernetesObjectsProvider;

// @public (undocumented)
export interface KubernetesObjectsProviderOptions {
  // (undocumented)
  config: Config;
  // (undocumented)
  customResources: k8sAuthTypes.CustomResource[];
  // (undocumented)
  fetcher: k8sAuthTypes.KubernetesFetcher;
  // (undocumented)
  logger: LoggerService;
  // (undocumented)
  objectTypesToFetch?: k8sAuthTypes.ObjectToFetch[];
  // (undocumented)
  serviceLocator: k8sAuthTypes.KubernetesServiceLocator;
}

// @public @deprecated (undocumented)
export type KubernetesObjectTypes = k8sAuthTypes.KubernetesObjectTypes;

// @public
const kubernetesPlugin: BackendFeature;
export default kubernetesPlugin;

// @public
export class KubernetesProxy {
  constructor(options: KubernetesProxyOptions);
  // (undocumented)
  createRequestHandler(
    options: KubernetesProxyCreateRequestHandlerOptions,
  ): RequestHandler;
}

// @public
export type KubernetesProxyCreateRequestHandlerOptions = {
  permissionApi: PermissionsService;
};

// @public
export type KubernetesProxyOptions = {
  logger: LoggerService;
  clusterSupplier: KubernetesClustersSupplier;
  authStrategy: AuthenticationStrategy;
  discovery: DiscoveryService;
  httpAuth?: HttpAuthService;
};

// @public @deprecated (undocumented)
export type KubernetesServiceLocator = k8sAuthTypes.KubernetesServiceLocator;

// @public @deprecated (undocumented)
export type ObjectFetchParams = k8sAuthTypes.ObjectFetchParams;

// @public (undocumented)
export type ObjectsByEntityRequest = KubernetesRequestBody;

// @public @deprecated (undocumented)
export type ObjectToFetch = k8sAuthTypes.ObjectToFetch;

// @public (undocumented)
export class OidcStrategy implements AuthenticationStrategy_2 {
  // (undocumented)
  getCredential(
    clusterDetails: ClusterDetails_2,
    authConfig: KubernetesRequestAuth,
  ): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(authMetadata: AuthMetadata_2): Error[];
}

// @public @deprecated (undocumented)
export interface RouterOptions {
  // (undocumented)
  catalogApi: CatalogApi;
  // (undocumented)
  clusterSupplier?: KubernetesClustersSupplier;
  // (undocumented)
  config: RootConfigService;
  // (undocumented)
  discovery: DiscoveryService;
  // (undocumented)
  logger: Logger;
  // (undocumented)
  permissions: PermissionEvaluator;
}

// @public (undocumented)
export class ServiceAccountStrategy implements AuthenticationStrategy_2 {
  // (undocumented)
  getCredential(
    clusterDetails: ClusterDetails_2,
  ): Promise<KubernetesCredential_2>;
  // (undocumented)
  presentAuthMetadata(_authMetadata: AuthMetadata_2): AuthMetadata_2;
  // (undocumented)
  validateCluster(): Error[];
}

// @public (undocumented)
export type ServiceLocatorMethod =
  | 'multiTenant'
  | 'singleTenant'
  | 'catalogRelation'
  | 'http';

// @public @deprecated (undocumented)
export type ServiceLocatorRequestContext =
  k8sAuthTypes.ServiceLocatorRequestContext;

// @public (undocumented)
export type SigningCreds = {
  accessKeyId: string | undefined;
  secretAccessKey: string | undefined;
  sessionToken: string | undefined;
};

// Warnings were encountered during analysis:
//
// src/auth/AksStrategy.d.ts:7:1 - (ae-undocumented) Missing documentation for "AksStrategy".
// src/auth/AksStrategy.d.ts:8:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/AksStrategy.d.ts:9:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/AksStrategy.d.ts:10:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/AnonymousStrategy.d.ts:6:1 - (ae-undocumented) Missing documentation for "AnonymousStrategy".
// src/auth/AnonymousStrategy.d.ts:7:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/AnonymousStrategy.d.ts:8:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/AnonymousStrategy.d.ts:9:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/AwsIamStrategy.d.ts:7:1 - (ae-undocumented) Missing documentation for "SigningCreds".
// src/auth/AwsIamStrategy.d.ts:16:1 - (ae-undocumented) Missing documentation for "AwsIamStrategy".
// src/auth/AwsIamStrategy.d.ts:21:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/AwsIamStrategy.d.ts:22:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/AwsIamStrategy.d.ts:24:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/AzureIdentityStrategy.d.ts:8:1 - (ae-undocumented) Missing documentation for "AzureIdentityStrategy".
// src/auth/AzureIdentityStrategy.d.ts:14:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/AzureIdentityStrategy.d.ts:15:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/AzureIdentityStrategy.d.ts:19:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/DispatchStrategy.d.ts:7:1 - (ae-undocumented) Missing documentation for "DispatchStrategyOptions".
// src/auth/DispatchStrategy.d.ts:19:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/DispatchStrategy.d.ts:20:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/DispatchStrategy.d.ts:21:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/GoogleServiceAccountStrategy.d.ts:6:1 - (ae-undocumented) Missing documentation for "GoogleServiceAccountStrategy".
// src/auth/GoogleServiceAccountStrategy.d.ts:7:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/GoogleServiceAccountStrategy.d.ts:8:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/GoogleServiceAccountStrategy.d.ts:9:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/GoogleStrategy.d.ts:7:1 - (ae-undocumented) Missing documentation for "GoogleStrategy".
// src/auth/GoogleStrategy.d.ts:8:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/GoogleStrategy.d.ts:9:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/GoogleStrategy.d.ts:10:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/OidcStrategy.d.ts:7:1 - (ae-undocumented) Missing documentation for "OidcStrategy".
// src/auth/OidcStrategy.d.ts:8:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/OidcStrategy.d.ts:9:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/OidcStrategy.d.ts:10:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/ServiceAccountStrategy.d.ts:6:1 - (ae-undocumented) Missing documentation for "ServiceAccountStrategy".
// src/auth/ServiceAccountStrategy.d.ts:7:5 - (ae-undocumented) Missing documentation for "getCredential".
// src/auth/ServiceAccountStrategy.d.ts:8:5 - (ae-undocumented) Missing documentation for "validateCluster".
// src/auth/ServiceAccountStrategy.d.ts:9:5 - (ae-undocumented) Missing documentation for "presentAuthMetadata".
// src/auth/types.d.ts:5:1 - (ae-undocumented) Missing documentation for "AuthenticationStrategy".
// src/auth/types.d.ts:9:1 - (ae-undocumented) Missing documentation for "KubernetesCredential".
// src/service/KubernetesBuilder.d.ts:14:1 - (ae-undocumented) Missing documentation for "KubernetesEnvironment".
// src/service/KubernetesBuilder.d.ts:15:5 - (ae-undocumented) Missing documentation for "logger".
// src/service/KubernetesBuilder.d.ts:16:5 - (ae-undocumented) Missing documentation for "config".
// src/service/KubernetesBuilder.d.ts:17:5 - (ae-undocumented) Missing documentation for "catalogApi".
// src/service/KubernetesBuilder.d.ts:18:5 - (ae-undocumented) Missing documentation for "discovery".
// src/service/KubernetesBuilder.d.ts:19:5 - (ae-undocumented) Missing documentation for "permissions".
// src/service/KubernetesBuilder.d.ts:20:5 - (ae-undocumented) Missing documentation for "auth".
// src/service/KubernetesBuilder.d.ts:21:5 - (ae-undocumented) Missing documentation for "httpAuth".
// src/service/KubernetesBuilder.d.ts:44:1 - (ae-undocumented) Missing documentation for "KubernetesBuilder".
// src/service/KubernetesBuilder.d.ts:45:5 - (ae-undocumented) Missing documentation for "env".
// src/service/KubernetesBuilder.d.ts:53:5 - (ae-undocumented) Missing documentation for "createBuilder".
// src/service/KubernetesBuilder.d.ts:55:5 - (ae-undocumented) Missing documentation for "build".
// src/service/KubernetesBuilder.d.ts:56:5 - (ae-undocumented) Missing documentation for "setClusterSupplier".
// src/service/KubernetesBuilder.d.ts:57:5 - (ae-undocumented) Missing documentation for "setDefaultClusterRefreshInterval".
// src/service/KubernetesBuilder.d.ts:58:5 - (ae-undocumented) Missing documentation for "setObjectsProvider".
// src/service/KubernetesBuilder.d.ts:59:5 - (ae-undocumented) Missing documentation for "setFetcher".
// src/service/KubernetesBuilder.d.ts:60:5 - (ae-undocumented) Missing documentation for "setServiceLocator".
// src/service/KubernetesBuilder.d.ts:61:5 - (ae-undocumented) Missing documentation for "setProxy".
// src/service/KubernetesBuilder.d.ts:62:5 - (ae-undocumented) Missing documentation for "setAuthStrategyMap".
// src/service/KubernetesBuilder.d.ts:65:5 - (ae-undocumented) Missing documentation for "addAuthStrategy".
// src/service/KubernetesBuilder.d.ts:66:5 - (ae-undocumented) Missing documentation for "buildCustomResources".
// src/service/KubernetesBuilder.d.ts:67:5 - (ae-undocumented) Missing documentation for "buildClusterSupplier".
// src/service/KubernetesBuilder.d.ts:68:5 - (ae-undocumented) Missing documentation for "buildObjectsProvider".
// src/service/KubernetesBuilder.d.ts:69:5 - (ae-undocumented) Missing documentation for "buildFetcher".
// src/service/KubernetesBuilder.d.ts:70:5 - (ae-undocumented) Missing documentation for "buildServiceLocator".
// src/service/KubernetesBuilder.d.ts:71:5 - (ae-undocumented) Missing documentation for "buildMultiTenantServiceLocator".
// src/service/KubernetesBuilder.d.ts:72:5 - (ae-undocumented) Missing documentation for "buildSingleTenantServiceLocator".
// src/service/KubernetesBuilder.d.ts:73:5 - (ae-undocumented) Missing documentation for "buildCatalogRelationServiceLocator".
// src/service/KubernetesBuilder.d.ts:74:5 - (ae-undocumented) Missing documentation for "buildHttpServiceLocator".
// src/service/KubernetesBuilder.d.ts:75:5 - (ae-undocumented) Missing documentation for "buildProxy".
// src/service/KubernetesBuilder.d.ts:76:5 - (ae-undocumented) Missing documentation for "buildRouter".
// src/service/KubernetesBuilder.d.ts:77:5 - (ae-undocumented) Missing documentation for "buildAuthStrategyMap".
// src/service/KubernetesBuilder.d.ts:80:5 - (ae-undocumented) Missing documentation for "fetchClusterDetails".
// src/service/KubernetesBuilder.d.ts:83:5 - (ae-undocumented) Missing documentation for "getServiceLocatorMethod".
// src/service/KubernetesBuilder.d.ts:84:5 - (ae-undocumented) Missing documentation for "getFetcher".
// src/service/KubernetesBuilder.d.ts:85:5 - (ae-undocumented) Missing documentation for "getClusterSupplier".
// src/service/KubernetesBuilder.d.ts:86:5 - (ae-undocumented) Missing documentation for "getServiceLocator".
// src/service/KubernetesBuilder.d.ts:87:5 - (ae-undocumented) Missing documentation for "getObjectsProvider".
// src/service/KubernetesBuilder.d.ts:88:5 - (ae-undocumented) Missing documentation for "getObjectTypesToFetch".
// src/service/KubernetesBuilder.d.ts:89:5 - (ae-undocumented) Missing documentation for "getProxy".
// src/service/KubernetesBuilder.d.ts:90:5 - (ae-undocumented) Missing documentation for "getAuthStrategyMap".
// src/service/KubernetesFanOutHandler.d.ts:9:22 - (ae-undocumented) Missing documentation for "DEFAULT_OBJECTS".
// src/service/KubernetesProxy.d.ts:50:5 - (ae-undocumented) Missing documentation for "createRequestHandler".
// src/service/router.d.ts:11:1 - (ae-undocumented) Missing documentation for "RouterOptions".
// src/service/router.d.ts:12:5 - (ae-undocumented) Missing documentation for "logger".
// src/service/router.d.ts:13:5 - (ae-undocumented) Missing documentation for "config".
// src/service/router.d.ts:14:5 - (ae-undocumented) Missing documentation for "catalogApi".
// src/service/router.d.ts:15:5 - (ae-undocumented) Missing documentation for "clusterSupplier".
// src/service/router.d.ts:16:5 - (ae-undocumented) Missing documentation for "discovery".
// src/service/router.d.ts:17:5 - (ae-undocumented) Missing documentation for "permissions".
// src/types/types.d.ts:9:1 - (ae-undocumented) Missing documentation for "ServiceLocatorMethod".
// src/types/types.d.ts:14:1 - (ae-undocumented) Missing documentation for "KubernetesObjectsProviderOptions".
// src/types/types.d.ts:15:5 - (ae-undocumented) Missing documentation for "logger".
// src/types/types.d.ts:16:5 - (ae-undocumented) Missing documentation for "config".
// src/types/types.d.ts:17:5 - (ae-undocumented) Missing documentation for "fetcher".
// src/types/types.d.ts:18:5 - (ae-undocumented) Missing documentation for "serviceLocator".
// src/types/types.d.ts:19:5 - (ae-undocumented) Missing documentation for "customResources".
// src/types/types.d.ts:20:5 - (ae-undocumented) Missing documentation for "objectTypesToFetch".
// src/types/types.d.ts:26:1 - (ae-undocumented) Missing documentation for "ObjectsByEntityRequest".
// src/types/types.d.ts:30:1 - (ae-undocumented) Missing documentation for "KubernetesObjectsProvider".
// src/types/types.d.ts:34:1 - (ae-undocumented) Missing documentation for "CustomResourcesByEntity".
// src/types/types.d.ts:39:1 - (ae-undocumented) Missing documentation for "AuthMetadata".
// src/types/types.d.ts:44:1 - (ae-undocumented) Missing documentation for "ClusterDetails".
// src/types/types.d.ts:49:1 - (ae-undocumented) Missing documentation for "KubernetesClustersSupplier".
// src/types/types.d.ts:53:1 - (ae-undocumented) Missing documentation for "KubernetesObjectTypes".
// src/types/types.d.ts:57:1 - (ae-undocumented) Missing documentation for "ObjectToFetch".
// src/types/types.d.ts:61:1 - (ae-undocumented) Missing documentation for "CustomResource".
// src/types/types.d.ts:65:1 - (ae-undocumented) Missing documentation for "ObjectFetchParams".
// src/types/types.d.ts:69:1 - (ae-undocumented) Missing documentation for "FetchResponseWrapper".
// src/types/types.d.ts:73:1 - (ae-undocumented) Missing documentation for "KubernetesFetcher".
// src/types/types.d.ts:77:1 - (ae-undocumented) Missing documentation for "ServiceLocatorRequestContext".
// src/types/types.d.ts:81:1 - (ae-undocumented) Missing documentation for "KubernetesServiceLocator".
```
