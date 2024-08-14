@Library('ot-central-ci') _
def cipipeline = new opstree.ci.templates.java_ci.java_ci()
node {
  
  cipipeline.call([

    // WORKSPACE MANAGEMENT
    clean_workspace: true,
    ignore_clean_workspace_failure:  false,
    delete_dirs: false,
    clean_when_build_aborted: true, 
    clean_when_build_failed: true,
    clean_when_not_built: true,
    clean_when_build_succeed: true,
    clean_when_build_unstable: true,

    // VCS MANAGEMENT 
    repo_https_url: "https://github.com/rajatvats-devops/spring3hibernate.git",
    repo_ssh_url: "git@github.com:rajatvats-devops/spring3hibernate.git",
    repo_branch: "master",
    repo_url_type: "http",
    jenkins_git_creds_id: "github-rajat",

     // Dependency Scanning
    dependency_check: true,
    dependency_scan_tool: "owasp",
    owasp_project_name: "owasp",
    owasp_report_publish: true,
    owasp_report_format: "html",
    fail_job_if_dependency_returned_exception: true,

    // Creds Scanning
    gitleaks_check: true,
    fail_job_if_leak_detected: false,
    gitleaks_report_format: "json",
    gitleaks_report_jenkins_publish: true,

    // Unit Testing
    unit_testing_check: false,
    fail_job_if_unit_issue_detected: true,
    build_tool: "maven",
    unit_test_reports_path: "**/target/surefire-reports/**.xml",
    findbugs_test_report_path: "**/target/findbugs/**.xml",
    withmaven_globaltool_jdk: "",
    withmaven_globaltool_maven: "",

    // Code Coverage
    code_coverage_check: true,

    // Static Code Analysis
    codebase_to_scan_directory: "**",
    static_code_analysis_check: true,
    path_to_sonar_properties: "sonar.properties",
    fail_job_if_analysis_returned_exception: true,
    jenkins_sonarqube_token_creds_id: "sonar-token",

    // Build Dockerfile
    perform_build_dockerfile: true,
  
    // Image scaning
    image_scanning_check: true,
    image_name: "spring3hibernate",
    image_tag: "latest",
    scan_severity: "CRITICAL",
    image_scanning_report_publish: true,

    // Publish Artifact(Docker Image)
    artifact_publish_check: true,
    artifact_destination_type: "ecr",
    jenkins_aws_credentials_id: "aws-rajat",
    docker_image_name: "spring3hibernate",
    docker_image_tag: "latest",
    ecr_repo_name: "spring3hibernate",
    ecr_region: "ap-south-1"
  ])

}
 
