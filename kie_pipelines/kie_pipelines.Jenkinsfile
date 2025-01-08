library identifier: 'cicd-shared-library@master', 
      retriever: modernSCM([$class: 'GitSCMSource', 
                           remote: 'https://github.com/purnima-jain/cicd-shared-library.git'])


// Hard-Coding Environment Variables - START
// env.CHANGE_AUTHOR = "Purnima Jain"
// env.CHANGE_BRANCH = "master"
// env.CHANGE_TARGET = "master"
env.ghprbAuthorRepoGitUrl = "https://github.com/purnima-jain/business-application-payments-daily.git"
// Hard-Coding Environment Variables - END

changeAuthor = getGroup() ?: env.CHANGE_AUTHOR
echo "changeAuthor: ${changeAuthor}"


def getGroup() {
    def group =getProjectGroupName(getProject())[0]
    echo "*group: ${group}"
    return group
}

def getProject() {
    def project = (ghprbAuthorRepoGitUrl =~ /((git|ssh|http(s)?)|(git@[\w\.]+))(:(\/\/)?(github.com\/))([\w\.@\:\/\-~]+)(\.git)(\/)?/)[0][8]
    echo "*project: ${project}"
    return project
}

def getProjectGroupName(String project, String defaultGroup = "purnima-jain") {
    def projectNameGroup = project.split("\\/")
    echo "projectNameGroup: ${projectNameGroup}"

    def group = projectNameGroup.size() > 1 ? projectNameGroup[0] : defaultGroup
    echo "**group: ${group}"

    def name = projectNameGroup.size() > 1 ? projectNameGroup[1] : project
    echo "name: ${name}"

    return [group, name]
}