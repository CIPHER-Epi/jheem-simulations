# Public artifact release contract

This repository is the organization-owned public archive for versioned JHEEM simulation inputs and
approved derived model artifacts. Git stores documentation and metadata; large artifacts are
attached to immutable GitHub Releases.

## Required release identity

- Use a unique semantic version or other immutable, project-approved version tag.
- Never delete and recreate a published tag or replace an asset under an existing release.
- Corrections receive a new version and identify the superseded release.
- Filenames must be deterministic and unambiguous within the release.
- An asset over GitHub's 2 GiB limit is split into numbered parts. The release notes record each part's SHA-256,
  the reassembled file's SHA-256, and the command that reassembles it.

## Required provenance

Every new release must document:

1. model and product identity;
2. artifact classification: source simulation input or derived public summary;
3. geographic and scenario coverage, sample count, and known omissions;
4. source release or dataset identities and their checksums;
5. generating code revision, runtime/container identity, and relevant manager bindings;
6. per-asset size and SHA-256 evidence;
7. scientific citation and contact information; and
8. explicit license or reuse terms. Repository visibility alone does not grant reuse rights.

Restricted managers, credentials, raw controlled data, and any artifact not approved for public
distribution must remain outside this repository.

## Staging before publication

A release may be staged as a GitHub draft before it can be published, for example the results of an
unpublished paper. A staged draft:

- is not public, not citable, and not part of the public record; nothing should depend on it;
- holds assets uploaded and verified the same way as for publication (inventory, per-asset size and
  SHA-256, verification from a fresh download);
- gathers its provenance in the draft notes;
- needs a license, citation, and public-data classification only at publication.

Its bytes don't change between staging and publication. If they must change, delete the draft and
stage again.

## Publication gate

Before publication, verify inventory, checksums, schema and numeric invariants, provenance,
public-data classification, and release metadata. Script what can be scripted: the inventory against
the source manifest, SHA-256 before upload and again from a fresh download, and a load check of a
sample of assets. The maintainer signs off, and the release notes record the results. An independent
reviewer is welcome but not required. Publication credentials should be organization-managed where
practical.

After publication, download the assets into a fresh location and repeat size and SHA-256
verification. Record corrections as new releases; do not mutate the published record.

Historical releases predate this contract and remain immutable. Improve their documentation through
committed audit records or release notes without replacing their bytes.
