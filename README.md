<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html>
<html b:css='false' b:defaultwidgetversion='2' b:layoutsVersion='3' b:responsive='true' b:templateUrl='unPlug' b:templateVersion='1.5.5' expr:dir='data:blog.languageDirection' expr:lang='data:blog.locale.language' xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
  <b:attr name='xmlns' value=''/>
  <b:attr name='xmlns:b' value=''/>
  <b:attr name='xmlns:expr' value=''/>
  <b:attr name='xmlns:data' value=''/>
  <b:attr cond='data:blog.locale.language == &quot;in&quot;' name='lang' value='id'/>
    
  <!--[ <head> open ]-->
  &lt;head&gt;

  <b:comment>Title that appears in search results</b:comment>
  <b:if cond='data:view.isMultipleItems'>
    <b:if cond='data:view.isHomepage'>
      <!--[ Homepage title ]-->
      <title><data:blog.title/></title>
      
      <b:elseif cond='data:view.search.query'/>
      <!--[ Search title ]-->
      <title><data:messages.search/>: <data:view.search.query/></title>
      
      <b:elseif cond='data:view.search.label'/>
      <!--[ Label title ]-->
      <title><data:blog.pageName/> - <data:blog.title/></title>
      
      <b:elseif cond='data:view.isArchive'/>
      <!--[ Archive title ]-->
      <title>Blog archive in: <data:blog.pageName/></title>
      
      <b:else/>
      <title>Blog - <data:blog.title/></title>
    </b:if>
    
    <b:elseif cond='data:view.isError'/>
    <!--[ Error title ]-->
    <title>Error 404: Not Found!</title>
    
    <b:else/>
    <!--[ SingleItem title ]-->
    <b:comment>It will omit the blog title when the character count exceeds 57</b:comment>
    <b:if cond='(data:blog.pageName.length + data:blog.title.length) gt 57'>
      <title><data:blog.pageName/></title>
      <b:else/>
      <title><data:blog.pageName/> - <data:blog.title/></title>
    </b:if>
  </b:if>

  <!--[ Meta for browser ]-->
  <meta charset='UTF-8'/>
  <meta content='width=device-width, initial-scale=1.0' name='viewport'/>
  <meta content='max-image-preview:large' name='robots'/>

  <!-- Link canonical -->
  <link expr:href='data:blog.url.canonical' rel='canonical'/>

  <b:if cond='!data:view.isError'>
    <!--[ Description and keyword ]-->
    <b:if cond='data:blog.metaDescription'>
      <meta expr:content='data:blog.metaDescription.escaped' name='description'/>
      <b:elseif cond='data:view.isSingleItem'/>
      <meta expr:content='data:post.snippet.escaped snippet { length: 147, links: false, linebreaks: false, ellipsis: false }' name='description'/>
      <b:else/>
      <meta expr:content='data:blog.pageName.escaped ? data:blog.pageName.escaped : data:blog.title.escaped' name='description'/>
    </b:if>
    <meta expr:content='data:blog.pageName.escaped ? data:blog.pageName.escaped : data:blog.title.escaped + &quot;, keyword_1, keyword_2, keyword_3 &quot;' name='keywords'/>
    <b:tag cond='data:view.isPost' expr:href='resizeImage(data:blog.postImageUrl, 0)' name='link' rel='image_src'/>
  
    <!--[ Generator and RRS ]-->
    <meta content='blogger' name='generator'/>
    <link expr:href='data:blog.homepageUrl.canonical + &quot;feeds/posts/default&quot;' expr:title='data:blog.title + &quot; - Atom&quot;' rel='alternate' type='application/atom+xml'/>
    <link expr:href='data:blog.homepageUrl.canonical + &quot;feeds/posts/default?alt=rss&quot;' expr:title='data:blog.title + &quot; - Feed&quot;' rel='alternate' type='application/rss+xml'/>
    <link expr:href='data:blog.homepageUrl.canonical + &quot;feeds/comments/default?alt=rss&quot;' expr:title='data:blog.title + &quot; - Comments Feed&quot;' rel='alternate' type='application/rss+xml'/>
  
    <!--[ Theme color ]-->
    <meta expr:content='data:skin.vars.themeColor' name='theme-color'/>
    <meta expr:content='data:skin.vars.themeColor' name='msapplication-navbutton-color'/>
    <meta expr:content='data:skin.vars.themeColor' name='apple-mobile-web-app-status-bar-style'/>
    <meta expr:content='true' name='apple-mobile-web-app-capable'/>
  
    <!--[ Favicon ]-->
    <link expr:href='data:blog.blogspotFaviconUrl' rel='apple-touch-icon' sizes='152x152'/>
    <link expr:href='data:blog.blogspotFaviconUrl' rel='icon' type='image/x-icon'/>
    <link expr:href='data:blog.blogspotFaviconUrl' rel='shortcut icon' type='image/x-icon'/>
    
    <!--[ Open graph and Twitter card ]-->
    <meta content='summary_large_image' name='twitter:card'/>
    <meta expr:content='data:blog.pageName.escaped ? data:blog.pageName.escaped : data:blog.title.escaped' property='og:title'/>
    <meta expr:content='data:blog.pageName.escaped ? data:blog.pageName.escaped : data:blog.title.escaped' name='twitter:title'/>
    <meta expr:content='data:blog.url.canonical' property='og:url'/>
    <meta expr:content='data:blog.url.canonical' name='twitter:url'/>
    <meta expr:content='data:blog.title.escaped' property='og:site_name'/>
    <b:if cond='data:view.isMultipleItems'>
      <meta content='website' property='og:type'/>
      <b:if cond='data:blog.metaDescription'>
        <meta expr:content='data:blog.metaDescription.escaped' property='og:description'/>
        <meta expr:content='data:blog.metaDescription.escaped' name='twitter:description'/>
        <b:else/>
        <meta expr:content='data:blog.pageName.escaped ? data:blog.pageName.escaped : data:blog.title.escaped' property='og:description'/>
        <meta expr:content='data:blog.pageName.escaped ? data:blog.pageName.escaped : data:blog.title.escaped' name='twitter:description'/>
      </b:if>
      <b:else/>
      <meta content='article' property='og:type'/>
      <b:if cond='data:blog.metaDescription'>
        <meta expr:content='data:blog.metaDescription.escaped' property='og:description'/>
        <meta expr:content='data:blog.metaDescription.escaped' name='twitter:description'/>
        <b:else/>
        <meta expr:content='data:post.snippet.escaped snippet { length: 147, links: false, linebreaks: false, ellipsis: false }' property='og:description'/>
        <meta expr:content='data:post.snippet.escaped snippet { length: 147, links: false, linebreaks: false, ellipsis: false }' name='twitter:description'/>
      </b:if>
    </b:if>
    <b:if cond='data:blog.postImageUrl'>
      <meta expr:content='resizeImage(data:blog.postImageUrl, 0)' property='og:image'/>
      <meta expr:content='resizeImage(data:blog.postImageUrl, 0)' name='twitter:image:src'/>
      <b:else/>
      
      <b:comment>Replace Add_your_image_url_here with your image url</b:comment>
      <b:with value='{url: &quot;Add_your_image_url_here&quot;}' var='thumb'>
        <meta expr:content='data:thumb.url' property='og:image'/>
        <meta expr:content='data:thumb.url' name='twitter:image:src'/>
      </b:with>
    </b:if>
    
    <!--[ Additional meta is here ]-->
    
  </b:if>
  <!--[ Median Ui v1.7 By MRSKT.COM ]-->
  <b:if cond='!data:view.isLayoutMode'>
    <!--[ CSS Stylesheet ]-->
    <b:if cond='!data:view.isPreview'>&lt;style&gt;/*</b:if><b:skin version='1.3.3'><![CDATA[
/*
<Group description="Address bar">
  <Variable name="themeColor" description="Address Bar Color" type="color" default="#3d73dd" value="#fffdfc"/>
</Group>

<Group description="Basic and color">
  <Variable name="fontSize" description="Basic font size" type="length" max="18px" default="14px" value="14px"/>
  <Variable name="themeLink" description="Link and button" type="color" default="#3740ff" value="#3740ff"/>
  <Variable name="themeC" description="Basic text color" type="color" default="#0e2045" value="#0e2045"/>
  <Variable name="themeC.alt" description="Alternative text color(opacity 80%)" type="color" default="#0e2045" value="#0e2045"/>
  <Variable name="themeBg" description="Basic background" type="color" default="#fffdfc" value="#fffdfc"/>
  <Variable name="themeBg.alt" description="Alternative background 01" type="color" default="#f9f9fb" value="#f9f9fb"/>
  <Variable name="themeBg.sec" description="Alternative background 02" type="color" default="#f5f3f2" value="#f5f3f2"/>
  <Variable name="themeBd.color" description="Default border-color" type="color" default="#e4e3e1" value="#e4e3e1"/>
</Group>

<Group description="Dark mode">
  <Variable name="darkLink" description="link and button(dark mode)" type="color" default="#8775f5" value="#8775f5"/>
  <Variable name="darkC" description="Text color(dark mode)" type="color" default="#d9e2f0" value="#d9e2f0"/>
  <Variable name="darkC.alt" description="Alternative text color(dark mode/opacity 70%)" type="color" default="#d9e2f0" value="#d9e2f0"/>
  <Variable name="darkBg" description="Basic dark background" type="color" default="#22262d" value="#22262d"/>
  <Variable name="darkBg.alt" description="Alternative dark background 01" type="color" default="#2d3138" value="#2d3138"/>
  <Variable name="darkBg.sec" description="Alternative dark background 02" type="color" default="#161c24" value="#161c24"/>
  <Variable name="darkBd.color" description="Basic dark border-color" type="color" default="#35393f" value="#35393f"/>
</Group>

<Group description="Button">
  <Variable name="buttonC" description="Button color" type="color" default="#fffdfc" value="#fffdfc"/>
  <Variable name="buttonBg" description="Button background" type="color" default="$(themeLink)" value="#3740ff"/>
  <Variable name="buttonBd.line" description="Button border-width" type="length" max="2px" default="1px" value="1px"/>
  <Variable name="buttonBd.radius" description="Button border-radius" type="length" max="20px" default="4px" value="4px"/>
  <Variable name="buttonBd.color" description="Button border-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
  <Variable name="button.maxWidth" description="Button max-width" type="length" max="420px" default="320px" value="320px"/>
</Group>

<Group description="Logo" selector="div.widget.Header">
  <Variable name="logo.maxWidth" description="Header image max-width" type="length" max="180px" default="160px" value="160px"/>
  <Variable name="logo.maxHeight" description="Header image max-height" type="length" max="$(headerHeight)" default="50px" value="50px"/>
</Group>

<Group description="Header" selector="header.mainH">
  <Variable name="headerHeight" description="Header max-height" type="length" max="100px" default="65px" value="65px"/>
  <Variable name="headerHeight.phone" description="Header max-height(mobile)" type="length" max="100px" default="65px" value="65px"/>
  <Variable name="headerC" description="Header color" type="color" default="$(themeC)" value="#0e2045"/>
  <Variable name="headerBg" description="Header background" type="color" default="$(themeBg)" value="#fffdfc"/>
  <Variable name="headerBd.line" description="Header border-width" type="length" max="2px" default="1px" value="1px"/>
  <Variable name="headerBd.radiusBL" description="Header border-radius(bottom-left/mobile only)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="headerBd.radiusBR" description="Header border-radius(bottom-right/mobile only)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="headerBd.color" description="Header border-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
</Group>

<Group description="Side navigation" selector="div.mainL">
  <Variable name="sideWidth.collapse" description="Side width(collapse)" type="length" max="100px" default="75px" value="75px"/>
  <Variable name="sideWidth.expand" description="Side width(expand)" type="length" max="300px" default="230px" value="230px"/>
  <Variable name="sideWidth.max" description="Side max-width(mobile only)" type="length" max="500px" default="480px" value="480px"/>
  <Variable name="sideMargin" description="Side margin(mobile only)" type="length" max="22px" default="0px" value="0px"/>
  <Variable name="sideC" description="Side color" type="color" default="$(themeC)" value="#0e2045"/>
  <Variable name="sideBg" description="Side background" type="color" default="$(themeBg)" value="#fffdfc"/>
  <Variable name="sideBd.line" description="Side border-width" type="length" max="2px" default="1px" value="1px"/>
  <Variable name="sideBd.radiusTL" description="Side border-radius(top-left/mobile only)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="sideBd.radiusTR" description="Side border-radius(top-right/mobile only)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="sideBd.radiusBL" description="Side border-radius(bottom-left/mobile only)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="sideBd.radiusBR" description="Side border-radius(bottom-right/mobile only)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="sideBd.color" description="Side border-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
</Group>

<Group description="Sidebar" selector="aside.sideB">
  <Variable name="sidebarWidth" description="Sidebar width" type="length" max="300px" default="280px" value="280px"/>
  <Variable name="sidebarPadding" description="Sidebar padding" type="length" max="15px" default="0px" value="0px"/>
  <Variable name="sidebarC" description="Sidebar color" type="color" default="$(themeC)" value="#0e2045"/>
  <Variable name="sidebarBg" description="Sidebar background" type="color" default="$(themeBg)" value="#fffdfc"/>
  <Variable name="sidebarBd.line" description="Sidebar border-width" type="length" max="2px" default="0px" value="0px"/>
  <Variable name="sidebarBd.radius" description="Sidebar border-radius" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="sidebarBd.color" description="Sidebar border-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
</Group>

<Group description="Content">
  <Variable name="content.maxWidth" description="Body max-width" type="length" max="1366px" default="1300px" value="1300px"/>
  <Variable name="contentPost.maxWidth" description="Post max-width" type="length" max="1024px" default="780px" value="780px"/>
  <Variable name="contentPage.maxWidth" description="Static page max-width" type="length" max="1024px" default="820px" value="820px"/>
  <Variable name="contentPop.maxWidth" description="Pop-up max-width" type="length" max="640px" default="550px" value="550px"/>
  <Variable name="contentPadding" description="Side spacing" type="length" max="30px" default="22px" value="22px"/>
  <Variable name="contentPadding.box" description="Content padding" type="length" max="15px" default="15px" value="15px"/>
  <Variable name="contentSpace" description="Content space-between" type="length" max="60px" default="40px" value="40px"/>
  <Variable name="contentC" description="Content color" type="color" default="$(themeC)" value="#0e2045"/>
  <Variable name="contentBg" description="Content background" type="color" default="$(themeBg)" value="#fffdfc"/>
  <Variable name="contentBg.alt" description="Content alternative background 01" type="color" default="$(themeBg.alt)" value="#f9f9fb"/>
  <Variable name="contentBg.sec" description="Content alternative background 02" type="color" default="$(themeBg.sec)" value="#f5f3f2"/>
  <Variable name="contentBd.line" description="Content border-width" type="length" max="2px" default="1px" value="1px"/>
  <Variable name="contentBd.radius" description="Content border-radius" type="length" max="20px" default="4px" value="4px"/>
  <Variable name="contentBd.radiusA" description="Content border-radius (alternative)" type="length" max="20px" default="10px" value="10px"/>
  <Variable name="contentBd.color" description="Content border-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
</Group>

<Group description="Footer" selector="footer.mainF">
  <Variable name="footerC" description="Footer color" type="color" default="$(themeC)" value="#0e2045"/>
  <Variable name="footerBg" description="Footer background" type="color" default="$(themeBg)" value="#fffdfc"/>
  <Variable name="footerBd.line" description="Footer border-width" type="length" max="2px" default="1px" value="1px"/>
  <Variable name="footerBd.radiusTL" description="Footer border-radius(top-left/mobile only)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="footerBd.radiusTR" description="Footer border-radius(top-right/mobile only)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="footerBd.color" description="Footer border-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
</Group>

<Group description="Post: Style" selector="div.blogP article.p">
  <Variable name="postPadding" description="Post padding" type="length" max="12px" default="0px" value="0px"/>
  <Variable name="postPadding.phone" description="post Padding(mobile only)" type="length" max="12px" default="0px" value="0px"/>
  <Variable name="postPadding.content" description="Post content padding" type="length" max="12px" default="0px" value="0px"/>
  <Variable name="postC" description="Post color" type="color" default="$(themeC)" value="#0e2045"/>
  <Variable name="postBg" description="Post background" type="color" default="$(themeBg)" value="#fffdfc"/>
  <Variable name="postBd.line" description="Post border-width" type="length" max="2px" default="0px" value="0px"/>
  <Variable name="postBd.radius" description="Post border-radius" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="postBd.color" description="Post border-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
  <Variable name="postBs.color" description="Post box-shadow background" type="color" default="transparent" value="transparent"/>
  <Variable name="postBs.hoverColor" description="Post box-shadow background(hover)" type="color" default="transparent" value="transparent"/>
</Group>

<Group description="Post: Component">
  <Variable name="noteC" description="Component: Note color" type="color" default="#272eb5" value="#272eb5"/>
  <Variable name="noteBg" description="Component: Note background" type="color" default="#e8f0fe" value="#e8f0fe"/>
  <Variable name="warnC" description="Component: Warning color" type="color" default="#e51661" value="#e51661"/>
  <Variable name="warnBg" description="Component: Warning background" type="color" default="#fce8e8" value="#fce8e8"/>
  <Variable name="stepC" description="Component: Step-list color" type="color" default="$(themeLink)" value="#3740ff"/>
  <Variable name="stepHover" description="Component: Step-list text(hover)" type="color" default="#fffdfc" value="#fffdfc"/>
</Group>

<Group description="Widget: Notification" selector="div.notify">
  <Variable name="notifHeight" description="Notif max-height" type="length" max="100px" default="55px" value="55px"/>
  <Variable name="notifLink" description="Link color" type="color" default="#3740ff" value="#3740ff"/>
  <Variable name="notifC" description="Text color" type="color" default="#272eb5" value="#272eb5"/>
  <Variable name="notifBg" description="Background color" type="color" default="#e8f0fe" value="#e8f0fe"/>
</Group>

<Group description="Widget: Mobile menu" selector="div.mainM">
  <Variable name="mobileHeight" description="max-height" type="length" max="100px" default="60px" value="60px"/>
  <Variable name="mobileMargin" description="Margin" type="length" max="22px" default="0px" value="0px"/>
  <Variable name="mobileC" description="Color" type="color" default="$(themeC)" value="#0e2045"/>
  <Variable name="mobileBg" description="Background" type="color" default="$(themeBg)" value="#fffdfc"/>
  <Variable name="mobileBd.line" description="Border-width" type="length" max="2px" default="0px" value="0px"/>
  <Variable name="mobileBd.radiusTL" description="Border-radius(top-left)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="mobileBd.radiusTR" description="Border-radius(top-right)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="mobileBd.radiusBL" description="Border-radius(bottom-left)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="mobileBd.radiusBR" description="Border-radius(bottom-right)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="mobileBd.color" description="Vorder-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
</Group>

<Group description="Widget: Table of Content">
  <Variable name="tocWidth" description="max-height" type="length" max="320px" default="280px" value="280px"/>
  <Variable name="tocMargin" description="Margin" type="length" max="22px" default="0px" value="0px"/>
  <Variable name="tocC" description="Color" type="color" default="$(themeC)" value="#0e2045"/>
  <Variable name="tocBg" description="Background" type="color" default="$(themeBg)" value="#fffdfc"/>
  <Variable name="tocBd.line" description="Border-width" type="length" max="2px" default="1px" value="1px"/>
  <Variable name="tocBd.radiusTL" description="Border-radius(top-left)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="tocBd.radiusTR" description="Border-radius(top-right)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="tocBd.radiusBL" description="Border-radius(bottom-left)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="tocBd.radiusBR" description="Border-radius(bottom-right)" type="length" max="20px" default="0px" value="0px"/>
  <Variable name="tocBd.color" description="Vorder-color" type="color" default="$(themeBd.color)" value="#e4e3e1"/>
</Group>

<Group description="(Do not edit) New Blogger comment required">
  <Variable name="body.background" description="Background" color="#989b9f" type="background" default="$(color) none repeat scroll center center"  value="$(color) url() no-repeat scroll center center"/>
  <Variable name="body.link.color" description="Link color" type="color" default="#989b9f"  value="#5b5c5e"/>
  <Variable name="body.text.font" description="Comment font size" type="font" default="400 14px sans-serif" value="400 13px sans-serif"/>
  <Variable name="body.text.color" description="Comment text color" type="color" default="#989b9f"  value="#6d7176"/>
  <Variable name="posts.background.color" description="Comment background color" type="color" default="#fffdfc"  value="transparent"/>
  <Variable name="posts.title.color" description="Post title color" type="color" default="#989b9f"  value="#5b5c5e"/>
  <Variable name="posts.icons.color" description="Post icons color" type="color" default="#989b9f" value="#5b5c5e"/>
  <Variable name="tabs.font" description="Tabs font" type="font" default="400 14px sans-serif" value="400 13px sans-serif"/>
  <Variable name="labels.background.color" description="Labels background color" type="color" default="#fff" value="#fffdfc"/>
</Group>
*/

/*
  THEME DETAILS:
  .
  Name      : Median UI
  Demo site   : median-ui.jagodesain.com
  Powered by    : jagodesain.com
  For     : blogger.com
  .
  ============================================================================
  NOTE:
  This theme is premium (paid). You can only get it by purchasing officially.
  If you get it for free through any method, that mean's you get it illegally.
  ============================================================================
*/

/* Variable */
:root{
/* var: Font */
--fontSize: $(fontSize) ;
--fontHead: 'Noto Sans', sans-serif ;
--fontBody: 'Noto Sans', sans-serif ;
--fontBody-alt: 'Fira Sans', sans-serif ;
--fontCode: 'Fira Mono', sans-serif ;

--head-H1: 2rem ;
--head-H2: 1.8rem ;
--head-H3: 1.7rem ;
--head-H4: 1.6rem ;
--head-H5: 1.5rem ;
--head-H6: 1.4rem ;
--head-fontWg: 400 ;
}
.nB{

/* var: Light-mode */
--lightLink: $(themeLink) ;
--lightC: $(themeC) ;
--lightC-alt: $(themeC.alt)cc ; /* cc mean's opacity 80% */
--lightBg: $(themeBg) ;
--lightBg-alt: $(themeBg.alt) ;
--lightBg-sec: $(themeBg.sec) ; 
--lightBg-pop: rgb(14 20 27 / 30%) ;
--lightBd-color: $(themeBd.color) ;

/* var: Dark-mode */
--darkLink: $(darkLink) ;
--darkC: $(darkC) ;
--darkC-alt: $(darkC.alt)B3 ;  /* B3 mean's opacity 70% */
--darkBg: $(darkBg) ;
--darkBg-alt: $(darkBg.alt) ;
--darkBg-sec: $(darkBg.sec) ;
--darkBg-pop: rgb(14 20 27 / 90%) ;
--darkBd-color: $(darkBd.color) ;

/* var: Theme */
--themeLink: var(--lightLink) ;
--themeC: var(--lightC) ;
--themeC-alt: var(--lightC-alt) ;
--themeBg: var(--lightBg) ;
--themeBg-alt: var(--lightBg-alt) ;
--themeBg-sec: var(--lightBg-sec) ;
--themeBg-pop: var(--lightBg-pop) ;
--themeBd-color: var(--lightBd-color) ;

/* var: Basic, button, input */
--vHeight: 100vh ;
--selectC: #fffdfc ;
--selectBg: var(--themeLink) ;
--placeHolder: var(--themeC-alt) ;

--buttonC: $(buttonC) ;
--buttonBg: $(buttonBg) ;
--buttonBd-line: $(buttonBd.line) ;
--buttonBd-color: $(buttonBd.color) ;
--buttonBd-radius: $(buttonBd.radius) ;
--button-maxWidth: $(button.maxWidth) ;

--inputC: currentColor ;
--inputBg: var(--themeBg) ;
--inputBd-line: 1px ;
--inputBd-color: var(--themeBd-color) ;
--inputBd-radius: 4px ;

/* var: Icons */
--iconWidth: 35px ;
--iconHeight: 35px ;

/* var: Pop-up */
--closeHeight-phone: 60px ;

/* var: Header */
--headerText-after: '' ;
--headerWidth-expand: var(--sideWidth-expand) ;
--headerHeight: $(headerHeight) ;
--headerHeight-min: -$(headerHeight) ;
--headerHeight-phone: $(headerHeight.phone) ;
--header-font: 1.143em ;
--header-fontWg: 500 ;
--headerC: $(headerC) ;
--headerBg: $(headerBg) ;
--headerBd-line: $(headerBd.line) ;
--headerBd-radiusBL: $(headerBd.radiusBL) ;
--headerBd-radiusBR: $(headerBd.radiusBR) ;
--headerBd-color: $(headerBd.color) ;
--headerLogo-maxWidth: $(logo.maxWidth) ;
--headerLogo-maxHeight: $(logo.maxHeight) ;

/* var: Sidenav */
--sideWidth: $(sideWidth.collapse) ;
--sideWidth-collapse: var(--sideWidth) ;
--sideWidth-expand: $(sideWidth.expand) ;
--sideWidth-max: $(sideWidth.max) ;
--sideMargin-phone: $(sideMargin) ;
--sideC: $(sideC) ;
--sideBg: $(sideBg) ;
--sideBd-line: $(sideBd.line) ;
--sideBd-radiusTL: $(sideBd.radiusTL) ;
--sideBd-radiusTR: $(sideBd.radiusTR) ;
--sideBd-radiusBR: $(sideBd.radiusBR) ;
--sideBd-radiusBL: $(sideBd.radiusBL) ;
--sideBd-color: $(sideBd.color) ;

/* var: Sidebar */
--sidebarWidth: $(sidebarWidth) ;
--sidebarPadding: $(sidebarPadding) ;
--sidebarC: $(sidebarC) ;
--sidebarBg: $(sidebarBg) ;
--sidebarBd-line: $(sidebarBd.line) ;             
--sidebarBd-radius: $(sidebarBd.radius) ;
--sidebarBd-color: $(sidebarBd.color) ;

/* var: Content */
--content-maxWidth: $(content.maxWidth) ;
--contentPost-maxWidth: $(contentPost.maxWidth) ;
--contentPage-maxWidth: $(contentPage.maxWidth) ;
--contentPop-maxWidth: $(contentPop.maxWidth) ;
--contentPadding: $(contentPadding) ;
--contentPadding-minus: -$(contentPadding) ;
--contentPadding-box: $(contentPadding.box) ;
--contentSpace: $(contentSpace) ;
--contentC: $(contentC) ;
--contentBg: $(contentBg) ;
--contentBg-alt: $(contentBg.alt) ;
--contentBg-sec: $(contentBg.sec) ;
--contentBd-line: $(contentBd.line) ;
--contentBd-radius: $(contentBd.radius) ;
--contentBd-radiusA: $(contentBd.radiusA) ;
--contentBd-color: $(contentBd.color) ;

/* var: Footer */
--footerC: $(footerC) ;
--footerBg: $(footerBg) ;
--footerBd-line: $(footerBd.line) ;
--footerBd-radiusTL: $(footerBd.radiusTL) ;
--footerBd-radiusTR: $(footerBd.radiusTR) ;
--footerBd-color: $(footerBd.color) ;

/* var: Post style */
--postPadding: $(postPadding) ;
--postPadding-phone: $(postPadding.phone) ;
--postPadding-content: $(postPadding.content) ;
--postC: $(postC) ;
--postBg: $(postBg) ;
--postBd-line: $(postBd.line) ;
--postBd-radius: $(postBd.radius) ;
--postBd-color: $(postBd.color) ;
--postBs-color: $(postBs.color) ;
--postBs-hoverColor: $(postBs.hoverColor) ;

/* var: Post font */
--postTitle-font: 2.6rem ;
--postTitle-fontPhone: 2rem ;
--postTitle-fontWg: 400 ;
--postTitle-fontItems: 1.2em ;
--postTitle-fontItemsPhone: 1.1em ;
--postDescription-font: 1.13rem ;
--postDescription-fontPhone: 1.072rem ;
--postBody-font: 1.143rem ;
--postBody-fontPhone: 1.072rem ;

/* var: Post typo */
--postBreak: 3em ;
--postImageBd-radius: 2px;
--lineHeight: 1.7 ;
--lineSpacing: 1.8em ;
--tableBg-color: rgb(246 246 246 / 80%) ;

/* var: Post thumbnail */
--thumbnailRatio: 56.25% ; /* According to aspect-ratio 16:9 (divide 9 by 16 = 0.5625) */
--thumbnailRatio-box: 100% ;

/* var: Post syntax */
--synC: #2f3337 ;
--synBg: #f8f9fa ;
--synOrange: #b75501 ;
--synBlue: #015692 ;
--synGreen: #54790d ;
--synRed: #f15a5a ;
--synGray: #656e77 ;
--synGold: #72621d ;
--synPurple: #803378 ;
--synBd-line: 1px ;
--synBd-radius: 4px ;
--synBd-color: #d2d3d7 ;

/* var: Post component */
--noteAfter: '\002A'  ;
--warnAfter: '\0021' ;
--noteC: $(noteC) ;
--noteBg: $(noteBg) ;
--warnC: $(warnC) ;
--warnBg: $(warnBg) ; /*#fef5fa*/
--stepC: $(stepC) ;
--stepHover: $(stepHover) ;

/* var: Widget */
--widgetTitle-font: 1.072rem ;
--widgetTitle-fontWg: 400 ;
--widgetTitle-afterD: inline-block ;
--widgetTitle-afterWd: 10px ;
--widgetTitle-afterC: var(--themeBd-color) ;
--widgetTitle-space: 20px ;

/* var: Widget notify */
--notifHeight: $(notifHeight) ;
--notifLink: $(notifLink) ;
--notifC: $(notifC) ;
--notifBg: $(notifBg) ;

/* var: Widget slider */
--sliderBd-radius: 4px ;
--sliderRatio: 43.75% ;

/* var: Widget featuredPosts */
--thumbnailSize: 300px ;

/* var: Widget mobileMenu */
--mobileHeight: $(mobileHeight) ;
--mobileMargin: $(mobileMargin) ;
--mobileC: $(mobileC) ;
--mobileBg: $(mobileBg) ;
--mobileBd-line: $(mobileBd.line) ;
--mobileBd-radiusTL: $(mobileBd.radiusTL) ;
--mobileBd-radiusTR: $(mobileBd.radiusTR) ;
--mobileBd-radiusBR: $(mobileBd.radiusBR) ;
--mobileBd-radiusBL: $(mobileBd.radiusBL) ;
--mobileBd-color: $(mobileBd.color) ;

/* var: Widget ToC */
--tocWidth: $(tocWidth) ;
--tocWidth-minus: -$(tocWidth) ;
--tocMargin: $(tocMargin) ;
--tocC: $(tocC) ;
--tocBg: $(tocBg) ;
--tocBd-line: $(tocBd.line) ;
--tocBd-radiusTL: $(tocBd.radiusTL) ;
--tocBd-radiusTR: $(tocBd.radiusTR) ;
--tocBd-radiusBR: $(tocBd.radiusBR) ;
--tocBd-radiusBL: $(tocBd.radiusBL) ;
--tocBd-color: $(tocBd.color) ;

/* var: Transition */
--tDuration: .1s ease ;
--tShowHide: opacity var(--tDuration), visibility var(--tDuration) ;

/* var: Bookmark */
--addBookmark: 'Save' ;
--removeBookmark: 'Saved' ;
--bookmarkTextLenght: 90px ;

/* var: Custom text */
--free: 'Free!' ;
--new: 'New!' ;
--breadcrumbs: '\005C' ;
--noImage: 'Null' ;
--labelComa: 'and' ;
--closeButton: 'Close' ;
--pageNext: 'Next' ;
--pagePrev: 'Back' ;
--latestUpdate: '\21BB' ;
--reply: 'Reply' ;
--replies: 'Write a reply...' ;
--readtimeBefore: '\00B7' ;
--readtimeAfter: 'min read' ;
--copyLink: 'or copy link' ;
--copied: 'Copied!' ;
--tableToc: 'Contents' ;
}
    /*]]></b:skin>

    <style>/*<![CDATA[*/
/* Font: Body + Heading, Noto Sans(Latin) by Google */ @font-face {font-family:'Noto Sans'; font-style:italic;font-weight:400;font-display:swap; src:url(https://fonts.gstatic.com/s/notosans/v27/o-0OIpQlx3QUlC5A4PNr4ARCQ_k.woff2) format('woff2'), url(https://fonts.gstatic.com/s/notosans/v27/o-0OIpQlx3QUlC5A4PNr4DRG.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Noto Sans'; font-style:italic;font-weight:500;font-display:swap; src:url(https://fonts.gstatic.com/s/notosans/v27/o-0TIpQlx3QUlC5A4PNr4AyxYOyDzW0.woff2) format('woff2'), url(https://fonts.gstatic.com/s/notosans/v27/o-0TIpQlx3QUlC5A4PNr4AyxYNyH.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Noto Sans'; font-style:italic;font-weight:600;font-display:swap; src:url(https://fonts.gstatic.com/s/notosans/v27/o-0TIpQlx3QUlC5A4PNr4AydZ-yDzW0.woff2) format('woff2'), url(https://fonts.gstatic.com/s/notosans/v27/o-0TIpQlx3QUlC5A4PNr4AydZ9yH.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Noto Sans'; font-style:italic;font-weight:700;font-display:swap; src:url(https://fonts.gstatic.com/s/notosans/v27/o-0TIpQlx3QUlC5A4PNr4Az5ZuyDzW0.woff2) format('woff2'), url(https://fonts.gstatic.com/s/notosans/v27/o-0TIpQlx3QUlC5A4PNr4Az5ZtyH.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Noto Sans'; font-style:normal;font-weight:400;font-display:swap; src:url(https://fonts.gstatic.com/s/notosans/v27/o-0IIpQlx3QUlC5A4PNr5TRA.woff2) format('woff2'), url(https://fonts.gstatic.com/s/notosans/v27/o-0IIpQlx3QUlC5A4PNb4Q.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Noto Sans'; font-style:normal;font-weight:500;font-display:swap; src:url(https://fonts.gstatic.com/s/notosans/v27/o-0NIpQlx3QUlC5A4PNjFhdVZNyB.woff2) format('woff2'), url(https://fonts.gstatic.com/s/notosans/v27/o-0NIpQlx3QUlC5A4PNjFhdlYA.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Noto Sans'; font-style:normal;font-weight:600;font-display:swap; src:url(https://fonts.gstatic.com/s/notosans/v27/o-0NIpQlx3QUlC5A4PNjOhBVZNyB.woff2) format('woff2'), url(https://fonts.gstatic.com/s/notosans/v27/o-0NIpQlx3QUlC5A4PNjOhBlYA.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Noto Sans'; font-style:normal;font-weight:700;font-display:swap; src:url(https://fonts.gstatic.com/s/notosans/v27/o-0NIpQlx3QUlC5A4PNjXhFVZNyB.woff2) format('woff2'), url(https://fonts.gstatic.com/s/notosans/v27/o-0NIpQlx3QUlC5A4PNjXhFlYA.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD}

/* Font: Body + Heading(Alternative), Fira Sans(Latin) by Google */ @font-face {font-family:'Fira Sans'; font-style:italic;font-weight:400;font-display:swap; src:url(https://fonts.gstatic.com/s/firasans/v16/va9C4kDNxMZdWfMOD5VvkrjJYTI.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firasans/v16/va9C4kDNxMZdWfMOD5VvkojN.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Fira Sans'; font-style:italic;font-weight:500;font-display:swap; src:url(https://fonts.gstatic.com/s/firasans/v16/va9f4kDNxMZdWfMOD5VvkrA6Qif4VFk.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firasans/v16/va9f4kDNxMZdWfMOD5VvkrA6Qhf8.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Fira Sans'; font-style:italic;font-weight:600;font-display:swap; src:url(https://fonts.gstatic.com/s/firasans/v16/va9f4kDNxMZdWfMOD5VvkrAWRSf4VFk.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firasans/v16/va9f4kDNxMZdWfMOD5VvkrAWRRf8.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Fira Sans'; font-style:italic;font-weight:700;font-display:swap; src:url(https://fonts.gstatic.com/s/firasans/v16/va9f4kDNxMZdWfMOD5VvkrByRCf4VFk.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firasans/v16/va9f4kDNxMZdWfMOD5VvkrByRBf8.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Fira Sans'; font-style:normal;font-weight:400;font-display:swap; src:url(https://fonts.gstatic.com/s/firasans/v16/va9E4kDNxMZdWfMOD5Vvl4jL.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firasans/v16/va9E4kDNxMZdWfMOD5Vfkw.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Fira Sans'; font-style:normal;font-weight:500;font-display:swap; src:url(https://fonts.gstatic.com/s/firasans/v16/va9B4kDNxMZdWfMOD5VnZKveRhf6.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firasans/v16/va9B4kDNxMZdWfMOD5VnZKvuQg.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Fira Sans'; font-style:normal;font-weight:600;font-display:swap; src:url(https://fonts.gstatic.com/s/firasans/v16/va9B4kDNxMZdWfMOD5VnSKzeRhf6.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firasans/v16/va9B4kDNxMZdWfMOD5VnSKzuQg.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD} @font-face {font-family:'Fira Sans'; font-style:normal;font-weight:700;font-display:swap; src:url(https://fonts.gstatic.com/s/firasans/v16/va9B4kDNxMZdWfMOD5VnLK3eRhf6.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firasans/v16/va9B4kDNxMZdWfMOD5VnLK3uQg.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD}

/* Font: Source code, Fira Mono(Latin) by Google */ @font-face {font-family:'Fira Mono'; font-style:normal;font-weight:400;font-display:swap; src:url(https://fonts.gstatic.com/s/firamono/v14/N0bX2SlFPv1weGeLZDtgJv7S.woff2) format('woff2'), url(https://fonts.gstatic.com/s/firamono/v14/N0bX2SlFPv1weGeLZDtQIg.woff) format('woff'); unicode-range:U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD}

/*! normalize.css v8.0.1 - modified for Jagodesain.com at 14px | MIT License | github.com/necolas/normalize.css*/ html{line-height:1.15;-webkit-text-size-adjust:100%} body{margin:0} main{display:block} h1{font-size:2em;margin:.67em 0} hr{box-sizing:content-box;overflow:visible} pre{font-family:monospace, monospace;font-size:.82em} a{background-color:transparent} abbr[title]{border-bottom:none;text-decoration:underline} b, strong{font-weight:bolder} code, kbd, samp{font-family:monospace, monospace;font-size:.88em} small{font-size:80%} sub, sup{font-size:75%;line-height:0;position:relative;vertical-align:baseline} sub{bottom:-.25em} sup{top:-.5em} img{border-style:none} button, input, optgroup, select, textarea{font-family:inherit;font-size:100%;line-height:1.15;margin:0;outline:0} button, input{overflow:visible} button, select{text-transform:none} button, [type=button], [type=reset], [type=submit]{-webkit-appearance:button} button::-moz-focus-inner, [type=button]::-moz-focus-inner, [type=reset]::-moz-focus-inner, [type=submit]::-moz-focus-inner{border-style:none;padding:0} button:-moz-focusring, [type=button]:-moz-focusring, [type=reset]:-moz-focusring, [type=submit]:-moz-focusring{outline:1px dotted ButtonText} fieldset{padding:.35em .75em .625em} legend{color:inherit;display:table;max-width:100%;padding:0;white-space:normal} progress{vertical-align:baseline} textarea{overflow:auto} [type=checkbox], [type=radio]{padding:0} [type=number]::-webkit-inner-spin-button,[type=number]::-webkit-outer-spin-button{height:auto} [type=search]{-webkit-appearance:textfield;outline-offset:-2px} [type=search]::-webkit-search-decoration{-webkit-appearance:none} ::-webkit-file-upload-button{-webkit-appearance:button;font:inherit} details{display:block} summary{display:list-item} template{display:none} [hidden], .hidden{display:none}

/* Basic: CSS */ ::selection{color:var(--selectC);background-color:var(--selectBg); opacity:.85} ::placeholder{color:var(--placeHolder)} ::before, ::after, *{-webkit-box-sizing:border-box;box-sizing:border-box} html{scroll-behavior:smooth;overflow-x:hidden; font:var(--fontSize) var(--fontBody)} body{position:relative; margin:0;padding:0 !important; color:var(--themeC);background-color:var(--themeBg); -webkit-font-smoothing: antialiased} h1, h2, h3, h4, h5, h6{margin-block:.67em; font:var(--head-fontWg) 1.4rem/1.4 var(--fontHead); color:currentColor} h1{font-size:var(--head-H1)} h2{font-size:var(--head-H2)} h3{font-size:var(--head-H3)} h4{font-size:var(--head-H4)} h5{font-size:var(--head-H5)} h6{font-size:var(--head-H6)} a{color:var(--themeLink);text-decoration:none} a:hover{filter:brightness(.9);transition:filter .1s} table{border-spacing:0} iframe{width:100%;border:0;margin-inline:auto} img{display:inline-block;max-width:100%;height:auto} svg{width:24px;height:24px; fill:currentColor} svg.line, svg .line{fill:none; stroke:currentColor;stroke-linecap:round;stroke-linejoin:round;stroke-width:1.25} .invisible{opacity:0;visibility:hidden} .clear{width:100%;display:block;margin:0;padding:0;float:none;clear:both} .break{word-break:break-word}

/* Basic: input and details tag */ input{color:var(--inputC);background-color:var(--inputBg)} input[type=search]::-ms-clear, input[type=search]::-ms-reveal{display:none;appearance:none;width:0;height:0} input[type=search]::-webkit-search-decoration, input[type=search]::-webkit-search-cancel-button, input[type=search]::-webkit-search-results-button, input[type=search]::-webkit-search-results-decoration{display:none;-webkit-appearance:none;appearance:none} details summary.n, details.sp summary, details.ac summary{list-style:none;outline:none; cursor:default} details summary.n::-webkit-details-marker, details.sp summary::-webkit-details-marker, details.ac summary::-webkit-details-marker{display:none} 

/* Basic: function */ .fc::after{content:''; display:block; position:fixed;top:0;left:0;right:0;bottom:0; z-index:1; transition:background var(--tDuration), var(--tShowHide), backdrop-filter var(--tDuration); background-color:transparent;opacity:0;visibility:hidden} .free::after, .new::after{display:inline-block; content:var(--free); color:var(--themeLink); font-weight:400;font-size:small; text-indent:5px} .new::after{content:var(--new)} .extL::after{content:''; display:inline-block; width:14px;height:14px;margin-inline-start:5px; background: url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23989b9f' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'><line x1='7' y1='17' x2='17' y2='7'/><polyline points='7 7 17 7 17 17'/></svg>") center / 16px no-repeat} .noList, .noList ul, .noList ol{list-style:none;margin:0;padding:0} .noWrap{white-space:nowrap} .ellips{white-space:nowrap;overflow:hidden;text-overflow:ellipsis} .cInherit a{color:inherit} .cInherit.u a:hover{text-decoration:underline} .bgInherit{background-color:inherit} .bgAlt{background-color:var(--themeBg-alt)} .clamp{/*display:-webkit-box;*/ -webkit-line-clamp:3;-webkit-box-orient:vertical;overflow:hidden} .strike{text-decoration:line-through} .flex{display:flex} .flex.center{align-items:center;justify-content:center} .flex.column{flex-direction:column} .flex.wrap{flex-wrap:wrap} .flex.space-between{justify-content:space-between} .flex.baseline{align-items:baseline} .flexIn{display:inline-flex} .flexIn.baseline{align-items:baseline} .flexIn.center{align-items:center} .shrink{flex-shrink:0} .grow{flex-grow:1} .opacity{opacity:.8} 

/* Font style */ .fontM{font-size:.93em} .fontS{font-size:small} .fontSm{font-size:smaller} .fontB{font-family:var(--fontBody)} .fontBa{font-family:var(--fontBody-alt)} .fontC{font-family:var(--fontCode)}
/* Icon and SVG */ .ic{display:inline-flex;flex-shrink:0;align-items:center;justify-content:center; width:var(--iconWidth);height:var(--iconHeight)} .op svg{opacity:.8} .i12 svg{flex-shrink:0; width:12px;height:12px} .i14 svg{flex-shrink:0; width:14px;height:14px} .i16 svg{flex-shrink:0; width:16px;height:16px} .i18 svg{flex-shrink:0; width:18px;height:18px} .i20 svg{flex-shrink:0; width:20px;height:20px} .i22 svg{flex-shrink:0; width:22px;height:22px} .i28 svg{flex-shrink:0; width:28px;height:28px}
/* Button */ .button{display:inline-flex;align-items:center;column-gap:8px; max-width:var(--button-maxWidth); padding:.75rem 1rem;outline:0;border:0;border-radius:var(--buttonBd-radius); color:var(--buttonC);background-color:var(--buttonBg); font:1rem/1.5 var(--fontBody); white-space:nowrap;overflow:hidden;text-overflow:ellipsis} .button:hover{filter:brightness(1.1)} .button:active{filter:brightness(.9)} .button.ln{border:var(--buttonBd-line) solid var(--buttonBd-color); color:inherit;background-color:transparent} .button.ln:hover{border-color:var(--buttonBg);box-shadow:0 0 0 .5px var(--buttonBg) inset} .button.sc{padding-inline:0; color:currentColor;background-color:transparent} .button.sc:hover{text-decoration:underline} .button.round{border-radius:30px} .button svg{flex-shrink:0; width:18px;height:18px} .button span::after{content:attr(data-text); display:block;font-size:smaller;text-indent:4px; opacity:.8} .btnF{display:flex;justify-content:center;gap:12px; margin-block:1em}

/* Avatar */ .avatar{min-width:28px;min-height:28px; border-radius:50%;background-color:var(--contentBg-sec);background-size:100%;background-position:center;background-repeat:no-repeat} .avatar.im{width:35px;height:35px}

/* Back to top */ .bT{align-items:center;gap:5px; position:relative;margin-inline-end:-2px} .bT::before{content:attr(data-text); opacity:.8}
/* Sticky ad */ .stickAd{position:fixed;left:0;bottom:0;right:0; min-height:70px;max-height:200px; padding:5px;border-top:1px solid var(--contentBd-color);background-color:var(--contentBg); transition:border var(--tDuration), padding var(--tDuration), min-height var(--tDuration); z-index:1} .stickAd .n{position:absolute;top:-28px;right:0; width:45px;height:28px; border-radius:10px 0 0;border:1px solid var(--contentBd-color);border-right:0;border-bottom:0; background-color:var(--contentBg)} .stickAd .n::after{content:'\2715';font-size:13px} .stickAd:not([open]){border-top:0;padding-block:0;min-height:0}
/* Error 404 */ .errorP{height:100vh;text-align:center} .errorC{width:calc(100% - calc(var(--contentPadding) * 2));max-width:450px; margin:auto; font-family:var(--fontBody-alt)} .errorC .e{font-size:4rem; color:rgb(0 0 0 / 10%)} .errorC .t{font-size:1.6rem} .errorC p{margin-block:25px 30px; line-height:1.4} .errorC .button{padding-inline:2.5em} .errorC .button::before{content:attr(aria-label)}

/* Notify */ .nB .fixN{--minHeight: 45px ; --minHeight-phone: var(--closeHeight-phone) ; display:inline-flex;align-items:center; position:fixed;bottom:calc(-100px + var(--contentPadding-minus));min-height:var(--minHeight); padding:15px 20px;border-radius:var(--contentBd-radius);color:#d9e2f0;background:#323232; font:small/1.3 var(--fontBody-alt); box-shadow:5px 10px 20px 0 rgb(0 0 0 / 10%); transition:bottom var(--tDuration), var(--tShowHide); z-index:99; animation:slideIn 2.2s ease-in forwards} .nB:not(.r) .fixN{left:var(--contentPadding);direction:ltr;} .nB.r .fixN{right:var(--contentPadding);direction:rtl} .fixN.copied::before{content:var(--copied)}
/* Widget: notify */ .notify{--padding:15px;--closeW:32px; color:var(--notifC);background-color:var(--notifBg)} .notify:not(.no-items){margin-block-end:var(--contentSpace)} .notify details{position:relative;min-height:0;padding-block:0;padding-inline-end:calc(var(--closeW) - 7px); transition:min-height var(--tDuration), padding var(--tDuration); overflow:hidden} .notify details[open]{min-height:var(--notifHeight);padding-block:var(--padding)} .notify summary{position:absolute;top:15px; width:var(--closeW);min-height:20px} .notify summary:not(.r){right:-7px} .notify summary.r{left:-7px} .notify summary .c::after{content:'\2715'; font-weight:400;font-size:14px} .notify .p{min-height:calc(var(--notifHeight) - (var(--padding) * 2)); line-height:1.3;font-family:var(--fontBody-alt)} .notify a:not(.b){color:var(--notifLink);text-decoration:underline; font-weight:500} .notify a.b{margin-inline-start:5px;padding:6px 8px;border-radius:var(--contentBd-radius);color:#3740ff;background-color:#fffdfc; box-shadow:0 10px 8px -8px rgb(0 0 0 / 12%)}

/* noScript/cookie */ body.nB .lazy:not([lazied]){display:none} .nJ{position:fixed;left:0;bottom:var(--contentPadding);right:0; max-width:400px;margin-inline:var(--contentPadding);padding:18px 20px;padding-block-end:36px;border-radius:var(--contentBd-radius); color:var(--warnC);background:var(--warnBg); font:small/1.3 var(--fontBody-alt);box-shadow:0 15px 30px -8px rgb(0 0 0 / 8%); z-index:99} .nJ:not([open]){display:none} .nJ summary{position:absolute;bottom:12px;right:20px} .nJ span:not(.c)::before{content:attr(data-text)} .nJ span.c{display:flex;align-items:center;gap:5px; font-weight:500} .nJ span.c::before{content:attr(data-text)} .nJs .noJava, .njs .lazyYt{display:none} .nJ.cookie:not(.hidden){display:block} .nJ.cookie{bottom:calc(-100px + var(--contentPadding)); margin-bottom:var(--contentPadding);padding-block-end:15px;color:#0e2045;background-color:#fffdfc; font-size:.94rem; box-shadow:0 15px 30px 8px rgb(0 0 0 / 8%); transition:bottom var(--tDuration), var(--tShowHide); animation:slideTop 2.2s ease-in forwards} .nJ.cookie p{margin-block:0 5px} .nJ.cookie p a:hover{text-decoration:underline; opacity:1} .nJ.cookie .ft{gap:20px;justify-content:flex-end; font-weight:500} .nJ.cookie .ft >*{padding-block:5px} .nJ.cookie .acc{color:var(--themeLink); cursor:pointer}

/* Element: po-up */ .popH{align-items:baseline;justify-content:space-between;column-gap:20px; top:0;left:0;right:0; padding-block:20px;background-color:inherit; z-index:3} .popH .filter{align-items:center;justify-content:flex-end;column-gap:10px;flex-shrink:0; min-width:50px} .popH .c{display:none; align-items:center;justify-content:center;gap:5px; width:var(--iconWidth);height:var(--iconHeight); margin-inline-end:-10px} .popH .c::after{content:'\2715'; font-weight:400;font-size:14px} .popH .t{display:none} .popH .t::before{content:attr(data-text); flex-grow:1; opacity:.8} .popUp .popH .c{display:flex} .popUp .popH .t{display:block} .popUp .popH{position:absolute; height:60px;padding:10px var(--contentPadding)} .popUp .popH .title{margin:0; font-size:1em} .popUp{display:flex;align-items:center;justify-content:center; position:fixed;left:0;right:0;bottom:0; width:100%;height:var(--vHeight); margin-bottom:-100%; font-size:1rem; opacity:0;visibility:hidden; transition:width var(--tDuration), height var(--tDuration), margin var(--tDuration), var(--tShowHide); z-index:20} .popUp .popIn{display:flex; position:relative; width:100%;max-width:var(--contentPop-maxWidth);max-height:calc(100% - (var(--contentPadding) * 2)); border:var(--contentBd-line) solid var(--contentBd-color);border-radius:var(--contentBd-radiusA); transition:inherit;z-index:3; overflow:hidden} .popUp .popC{width:100%; padding:60px var(--contentPadding) var(--contentPadding); background-color:var(--contentBg); overflow-y:scroll;overflow-x:hidden} .popI:checked ~ .popUp{opacity:1;visibility:visible; margin-bottom:0} .popI:checked ~ .popUp .fc::after{opacity:1;visibility:visible; background-color:var(--themeBg-pop); backdrop-filter:saturate(180%) blur(10px)}

/* element: Main */ .maxC{margin-inline:auto;padding-inline:var(--contentPadding); max-width:var(--content-maxWidth)} .mainH{--gapH:15px;gap:var(--gapH); height:var(--headerHeight); position:-webkit-sticky;position:sticky;top:0; border-bottom:var(--headerBd-line) solid var(--headerBd-color); color:var(--headerC);background-color:var(--headerBg); z-index:10} .mainN{min-height:calc(var(--vHeight) - var(--headerHeight)); transition:min-height var(--tDuration)} .mainF{position:relative; margin-block-start:auto; padding-block:25px;border-radius:var(--footerBd-radiusTL) var(--footerBd-radiusTR) 0 0;color:var(--footerC);background-color:var(--footerBg)}

/* mainH */ .mainH >*{align-items:center} .headL{--gap: 10px; gap:var(--gap); width:var(--headerWidth-expand)} .headR{--gap: 15px; flex-grow:1;gap:var(--gap); width:calc(100% - (var(--headerWidth-expand) + var(--gapH))); padding-inline-end:var(--contentPadding)} .headT{max-width:calc(100% - (((var(--sideWidth) - var(--iconWidth)) / 2) + var(--iconWidth) + var(--gap)))} .headB{position:relative;margin-inline-start:auto}

/* mainH: icon */ .headi.menu{height:100%; padding-inline-start:calc((var(--sideWidth) - var(--iconWidth)) /2)} .headi:not(.menu){align-items:center;justify-content:flex-end;gap:2px; position:relative;margin-inline-end:-8px} .headi .sc{display:none} .ibook .bc{position:relative} .ibook .bc svg{z-index:-1} .ibook .bc::before{content:attr(data-text); display:flex;align-items:center;justify-content:center; position:absolute;top:1px;right:2px;min-width:18px;height:18px; border-radius:20px;color:var(--themeLink);background-color:var(--headerBg); font-weight:500;font-size:10px;font-style:normal}

/* mainH: setting */ .settB{--maxWidth: 260px; --maxWidth-minus: -260px} .settB .h{align-items:center;align-self:flex-start;gap:6px; padding-top:var(--contentPadding-box)} .settB .h::after{content:attr(data-text)} .settB .h svg{display:none} .setti{--gap:15px; flex-wrap:wrap; gap:var(--gap)} .setti >*{width:calc((100% / 5) - (var(--gap) * 4/5))} .ipopUp{position:absolute;top:0; width:var(--maxWidth);padding:var(--contentPadding-box);border:var(--contentBd-line) solid var(--contentBd-color);border-radius:var(--contentBd-radiusA);background-color:var(--contentBg); transition:top var(--tDuration), left var(--tDuration), right var(--tDuration), var(--tShowHide); box-shadow:0 10px 30px -8px rgb(0 0 0 / 15%); overflow:hidden; z-index:1} .ipopUp:not(.r){right:0} .ipopUp.r{left:0} /* set theme or bookmark */ .iTheme, .iBook{gap:15px; padding-top:0} .inn{--gap: 10px; flex-wrap:wrap;gap:12px var(--gap)} .inn >*:not(:last-child){width:calc((100% / 3) - (var(--gap) * 2/3));transition:font-weight var(--tDuration), color var(--tDuration), opacity var(--tDuration)} .inn >*:not(:last-child):hover{opacity:.8} .inn >*:last-child{width:100%} .inn >*:not(:last-child)::after{white-space:nowrap;overflow:hidden;text-overflow:ellipsis} .inn >*::after{content:attr(data-text); display:block} .inn .i{height:36px;margin-bottom:6px;border-radius:calc(var(--contentBd-radiusA) /1.5); background-color:#e5e5e6;overflow:hidden; transition:box-shadow var(--tDuration)} .inn .i >*{flex:1 0 50%; padding-inline-start:6px;padding-block-start:6px} .inn .k{gap:7px; height:100%;padding-block:8px 0;padding-inline:8px;background-color:#fffdfc} .inn .k:not(.r){border-top-left-radius:calc(var(--contentBd-radiusA) /2.2)} .inn .k.r{border-top-left-radius:0;border-top-right-radius:calc(var(--contentBd-radiusA) /2.2)} .inn .k >*{gap:4px;width:100%} .inn .k >*::before, .inn .k >*::after{content:'';flex-shrink:0;width:12px;height:1px; background-color:rgb(0 0 0 / 60%)} .inn .p::before{width:100%} .inn .p::after{width:60%} .inn .a >*:not(:first-child), .inn .a >*:not(:first-child) .k{padding-inline-start:0} .inn .a >*:not(:first-child) .k:not(.r), .inn .a >*:not(:first-child) .k.r{border-radius:0} .inn .a >*:first-child .k{padding-inline-end:0} .inn .a >*:first-child .t::after{flex-grow:1;width:3px} .inn .a >*:first-child .p::after{width:100%} .inn .a >*:not(:first-child) .t::before, .inn .a >*:not(:first-child) .p::after{width:8px} .inn .a >*:not(:first-child) .t::after{display:none} .inn .rev{background-color:#22262d} .inn .rev .k{background-color:#5a5c63} .inn .rev .k >*::before, .inn .rev .k >*::after{background-color:#d9e2f0} /* set theme or bookmark: active */ .setI:checked ~ .settB .iSett, .setI:checked ~ .settB .iTheme, .setI:checked ~ .settB .iBook, .darkI:checked ~ .settB .iTheme, .bookI:checked ~ .settB .iBook{top:5px} .setI:checked ~ .settB .iSett, .darkI:checked ~ .settB .iTheme, .bookI:checked ~ .settB .iBook, .setI:checked ~ .section .st.fc::after, .darkI:checked ~ .section .dc.fc::after, .bookI:checked ~ .section .bc.fc::after, .setI:checked ~ .darkI:checked ~ .section .dc.fc::after, .setI:checked ~ .bookI:checked ~ .section .bc.fc::after{opacity:1;visibility:visible} .setI:checked ~ .settB .iTheme .h svg, .setI:checked ~ .settB .iBook .h svg{display:block} .setI:checked ~ .settB .iTheme:not(.r), .setI:checked ~ .settB .iBook:not(.r){right:var(--maxWidth-minus)} .setI:checked ~ .settB .iTheme.r, .setI:checked ~ .settB .iBook.r{left:var(--maxWidth-minus)} .setI:checked ~ .darkI:checked ~ .settB .iTheme:not(.r), .setI:checked ~ .bookI:checked ~ .settB .iBook:not(.r){right:0} .setI:checked ~ .darkI:checked ~ .settB .iTheme.r, .setI:checked ~ .bookI:checked ~ .settB .iBook.r{left:0} .setI:checked ~ .darkI:checked ~ .section .dc.fc::after, .setI:checked ~ .bookI:checked ~ .section .bc.fc::after{z-index:2}

/* mainH: Bookmark */ .addb ~ label svg{display:none} .addb:not(:checked) ~ label svg:nth-child(1), .addb:checked ~ label svg:nth-child(2){display:block} .addb:checked ~ label svg, .book .bm-delete:hover{color:var(--themeLink); opacity:1}
.addl .addb:checked ~ label::before{content:var(--removeBookmark)}
.addl label::before{content:var(--addBookmark); position:relative;max-width:0;padding-inline:0; transition:max-width var(--tDuration), padding-inline var(--tDuration); opacity:.8; white-space:nowrap;overflow:hidden;text-overflow:ellipsis} 
.addl:hover label::before{max-width:var(--bookmarkTextLenght);padding-inline:4px 3px; opacity:1}
.iBook{padding:0} .iBook:not(.item) >*{padding-inline:var(--contentPadding-box)} .iBook .bookmark-inner{gap:20px; max-height:300px;padding-block-end:var(--contentPadding-box);overflow-x:hidden;overflow-y:scroll} .iBook .loading{gap:8px} .iBook .loading::after{content:attr(data-text)} .book{--thumbSize: 50px; gap:14px} .book >.flex{gap:10px;align-items:center} .book .bm-thumb{position:relative;width:var(--thumbSize); opacity:.8} .book .bm-thumb a{display:block;position:inherit; padding-top:var(--thumbnailRatio-box); border-radius:var(--contentBd-radius);background-color:var(--contentBg-alt); overflow:hidden} .book .bm-im{position:absolute;top:0;left:0;bottom:0;right:0; background-size:cover;background-position:center;background-repeat:no-repeat; font-size:10px;line-height:1.1} .book .bm-title{font: .95rem/1.3 var(--fontBody-alt)} .book .bm-title a{display:-webkit-box; -webkit-line-clamp:3} .book .bm-title a:hover, .book ~ .more:hover span:not(.fontSm){text-decoration:underline} .book .bm-delete{padding:5px;padding-inline-end:0; cursor:pointer} .book ~ .more span:not(.fontSm){margin-inline-end:6px;color:var(--themeLink)} .book.all{--gap:16px; --thumbSize:60px; gap:var(--gap)} .book.all >.flex{gap:15px; width:calc((100% / 2) - (var(--gap) / 2)); padding:15px;border:1px solid var(--contentBd-color);border-radius:var(--contentBd-radius);background-color:var(--contentBg); transition:border-color var(--tDuration), box-shadow var(--tDuration); overflow:hidden} .book.all >.flex:hover{border-color:var(--themeLink); box-shadow:0 0 0 .5px var(--themeLink) inset, 0 25px 60px -20px rgb(0 0 0 / 20%)} .book.all .bm-thumb{opacity:1} .book.all .bm-title{font-size:1.15rem} .book.all .bm-delete{padding:8px} @media screen and (max-width:640px){.book.all{--gap:14px} .book.all >.flex{width:100%}} @media screen and (max-width:500px){.book.all >.flex{gap:12px; padding:10px} .book.all .bm-title{font-size:1.05rem}}

/* mainN */ .mainL{position:relative;width:var(--sideWidth-collapse); z-index:1; transition:width var(--tDuration)} .mainR{width:calc(100% - var(--sideWidth-collapse))} .leftW{height:var(--vHeight);color:var(--sideC);background-color:var(--sideBg); transition:height var(--tDuration)} .leftC{padding-inline:calc((var(--sideWidth) - var(--iconWidth)) /2)} .leftN{width:100%;height:100%; padding-block:var(--contentPadding-box) var(--closeHeight-phone);background-color:inherit} .leftP{position:absolute;left:0;bottom:0;right:0; padding-block:18px;background-color:inherit}

/* mainN: menu */ .leftNav{--padding:10px} .leftNav:not(.r) .a::before{right:calc(var(--contentPadding-minus) + 3px); border-radius:2px 0 0 2px} .leftNav.r .a::before{left:calc(var(--contentPadding-minus) + 3px); border-radius:0 2px 2px 0} .leftNav .a::before{content:''; position:absolute;top:0;bottom:0; border-inline-start:2px solid var(--themeLink); opacity:0;visibility:hidden; transition:var(--tShowHide)} .leftNav .a{ align-items:center;position:relative; min-width:var(--iconWidth);padding-block:var(--padding); filter:none} .leftNav .a svg{flex-shrink:0} .leftNav .a svg.r{width:14px;height:14px; margin-inline-start:auto} .leftNav .a >svg{margin-inline-start:calc((var(--iconWidth) - 20px) / 2);margin-inline-end:calc(((var(--iconWidth) - 20px) / 2) + 10px - calc((var(--iconWidth) - 20px) / 2))} .leftNav .a >.text{padding-inline-start:calc((var(--iconWidth) - 20px) / 2)} .leftNav .a:hover >svg, .leftNav .a.home >svg{color:var(--themeLink)} .leftNav .a:hover::before, .leftNav details[open] .a::before, .leftNav .a.home::before{opacity:.8;visibility:visible} .leftNav .br::after{content:''; display:block;margin-block:12px; border-bottom:var(--sideBd-line) solid var(--sideBd-color)} .leftNav details[open] svg.r{transform:rotate(180deg)} .leftNav details .n{padding-block:5px 10px;padding-inline-start:calc(var(--iconWidth) - 15px);overflow:hidden} .leftNav details .n li{position:relative;padding-inline-start:calc((var(--iconWidth) - 20px) + 10px)} .leftNav details .n li >*{display:inline-block;padding-block:4px} .leftNav details .n li::after{content:''; position:absolute;top:-85px; width:14px;height:100px;border-inline-start:1.5px solid var(--sideBd-color);border-block-end:1.5px solid var(--sideBd-color)} .leftNav:not(.r) details .n li::after{left:0; border-radius:0 0 0 8px} .leftNav.r details .n li::after{right:0; border-radius:0 0 8px 0} .leftNav details .n li.m::before{content:attr(data-text); display:block;margin-block:15px 8px; font-size:smaller;opacity:.6} .leftNav details .n li.m::after{height:124px} .addNav li:not(:last-child)::after{content:'\00B7';margin-inline:8px}

/* mainC */ .mainAd:not(.no-items){margin-block-end:var(--contentSpace)} .mainC{padding-block-end:var(--contentSpace)} .mainC >.maxC{margin-block-start:var(--contentPadding)} .mainB{justify-content:center;gap:var(--contentSpace)} .mainB .blogB{width:calc(100% - (var(--sidebarWidth) + var(--contentSpace))); transition:width var(--tDuration), max-width var(--tDuration)} .mainB .blogB.item{max-width:var(--contentPost-maxWidth)} .mainB .blogB.static{max-width:var(--contentPage-maxWidth)} .mainB .sideB{gap:var(--contentSpace);width:var(--sidebarWidth); max-width:500px} .mainB .sideSticky{position:-webkit-sticky; position:sticky;top:calc(var(--headerHeight) + 10px)} .mainB .sideB .section:not(.slider){gap:0} .mainB .sideB .widget:not(:first-child){margin-top:var(--contentSpace)} .mainB .sideB #HTML11{margin-top:0} .mainB .section:not(.slider){gap:var(--contentSpace)} .mainB.full :is(.blogB, .sideB){width:100%} .blogB >.section:not(:last-child){margin-bottom:var(--contentSpace)}

/* mainM */ .mainM{display:none; position:fixed;left:var(--mobileMargin);bottom:var(--mobileMargin);right:var(--mobileMargin); border-top:var(--mobileBd-line) solid var(--mobileBd-color);border-radius:var(--mobileBd-radiusTL) var(--mobileBd-radiusTR) var(--mobileBd-radiusBR) var(--mobileBd-radiusBL); color:var(--mobileC);background-color:var(--mobileBg); box-shadow:0 -10px 25px -5px rgb(0 0 0 / 10%);z-index:1} .mobileM{height:var(--mobileHeight);padding-inline:var(--contentPadding); font-size:9px} .mobileM >*{justify-content:center;width:20%} .mobileM *[data-text]{justify-content:center; min-width:40px;max-width:100px;min-height:35px} .mobileM *[data-text]::after{content:attr(data-text); display:block;width:100%; text-align:center; white-space:nowrap;overflow:hidden;text-overflow:ellipsis} .mobileM.index .search:nth-last-child(2){order:3}

/* mainF */ .mainF::before{content:'';position:absolute;top:0;left:var(--contentPadding);right:var(--contentPadding);border-block-start:var(--footerBd-line) solid var(--footerBd-color)} .mainF .credits{align-items:center;gap:10px} .mainF .HTML{margin-inline-end:auto; overflow:hidden;text-overflow:ellipsis} .mainF .credit, .mainF .credit .e{display:inline} .mainF .credit .creator{opacity:0} .mainF .credit .e::before{content:'\00A9'} .mainF .socials{position:relative; margin-inline-end:-6px} .mainF .socials div.ic{opacity:.5} .mainF .socials .ic{width:30px;height:30px}

/* Widget: default */ .widget .title{position:relative;margin-block:0 var(--widgetTitle-space); font-weight:var(--widgetTitle-fontWg);font-size:var(--widgetTitle-font)} .widget .title.s{font-size:small} .widget .title::after{content:''; display:var(--widgetTitle-afterD);vertical-align:middle; width:var(--widgetTitle-afterWd);margin-inline-start:8px;border-bottom:1px solid var(--widgetTitle-afterC); opacity:1} .no-items{display:none}

/* Widget: Header */ .Header{width:100%;background-repeat:no-repeat;background-size:100%;background-position:center} .Header img{max-width:var(--headerLogo-maxWidth);max-height:var(--headerLogo-maxHeight)} .Header a:hover{opacity:1} .headN{display:block;margin:0; font-weight:var(--header-fontWg);font-size:var(--header-font)} .headt{display:block} .headt::after{content:var(--headerText-after); display:inline-block;font-weight:400;font-size:11px;line-height:14px; opacity:.8}

/* Widget: BlogSearch */ .BlogSearch form{position:relative; margin-inline:-10px;border-radius:var(--contentBd-radiusA);background-color:transparent;overflow:hidden} .BlogSearch input[type=search]{display:block; width:320px;height:42px; padding-inline:40px;border:0; transition:margin var(--tDuration), padding-inline var(--tDuration), background var(--tDuration)} .BlogSearch .b{position:absolute;top:0;bottom:0;min-width:40px; padding:0;border:0; transition:var(--tShowHide)} .BlogSearch .ba:not(.r), .BlogSearch .bu.r{left:0} .BlogSearch .ba.r, .BlogSearch .bu:not(.r){right:0} .BlogSearch .bu::before{content:'\2715';font-size:13px} .BlogSearch:focus-within .b.bu{opacity:1;visibility:visible; color:inherit} .BlogSearch:focus-within input, .BlogSearch:hover input{background-color:var(--contentBg-sec)} 

/* Widget: Profile */ .proP:checked ~ .profileIcon .fc::after, .proP:checked ~ .profilePop{opacity:1;visibility:visible} .proT:not(:checked) ~ .t.clamp{display:-webkit-box} .proT:not(:checked) ~ label{display:inline-block} .proT:not(:checked) ~ .proTeam >*:not(.s){display:none} .profileIcon .a span.p::before, .Profile .location::after, .profilePop label::before{content:attr(data-text)} .profileIcon .a{align-items:center} .profileIcon .a span.p{margin-inline-start:6px} .profileIcon .n{max-width:calc(100% - 45px)} .profileIcon .avatar{margin-inline-start:calc((var(--iconWidth) - 20px) / 2 - 4px);margin-inline-end:calc(((var(--iconWidth) - 20px) / 2) + 6px)} .profileIcon.team .avatar, .profileIcon.team .avi{min-width:32px;min-height:32px; margin-inline-start:calc((var(--iconWidth) - 20px) / 2 - 6px);margin-inline-end:0;border:2px solid var(--sideBg)} .profileIcon.team .avatar:not(:first-child){margin-inline-start:-8px} .profileIcon.team .avi{display:none;border-width:0} .profilePop{position:absolute;bottom:var(--contentPadding); width:220px;min-height:160px;max-height:220px;border:var(--contentBd-line) solid var(--contentBd-color);border-radius:var(--contentBd-radiusA);background-color:var(--contentBg); box-shadow:0 25px 60px -20px rgb(0 0 0 / 20%);transition:var(--tShowHide);z-index:1; overflow:hidden} .profilePop:not(.r){left:var(--contentPadding)} .profilePop.r{right:var(--contentPadding)} .profilePop.team{--padding:15px;--padding-minus:-15px; padding:var(--padding)} .profilePop .h{gap:10px;padding:15px} .profilePop .h .n{width:calc(100% - (28px + 10px))} .profilePop .d{padding:0 15px 15px} .profilePop .d a{text-decoration:underline} .profilePop label{display:none;padding-block-start:5px; color:var(--themeLink)} .proTeam{width:100%;overflow-x:hidden;overflow-y:auto} .proTeam .team >*{--gap:10px; align-items:center;gap:var(--gap); position:relative; width:calc(100% + (var(--padding) * 2));margin-inline:var(--padding-minus); padding:5px var(--padding)} .proTeam .team >*::after{content:attr(data-text);flex:1 0 calc(100% - (35px + var(--gap))); /*white-space:nowrap;*/ text-overflow:ellipsis;overflow:hidden; display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical} .proTeam .team .avatar{width:35px;height:35px}

/* Widget: Sliders */ .slideB{border-radius:var(--sliderBd-radius);overflow:hidden} .slideB:hover .slideI svg{opacity:1;visibility:visible} .slideB:hover .slideI svg .pause{display:block} .slideB:hover .slideI svg .play, .slideI svg .pause{display:none} .slideB:hover .slider, .slideB:hover .slideI .i{animation-play-state:paused} .slider.no-items ~ .slideI{display:none} .slideI{--height:12px;--dotHeight:4px;gap:5px; position:relative;height:var(--height); margin-block:5px calc(var(--contentSpace) - (var(--height) - var(--dotHeight)))} .slideI .i{width:var(--dotHeight);height:var(--dotHeight); border-radius:10px;background-color:rgb(0 0 0 / 15%);transition: width var(--tDuration), background-color var(--tDuration)} .slideI:not(.r) svg{right:0} .slideI.r svg{left:0} .slideI svg{position:absolute;top:0; opacity:0;visibility:hidden; transition: opacity var(--tDuration) .4s, visibility var(--tDuration) .4s} .slideI .i:nth-child(1){animation: bullet 16.4s ease 0ms infinite} .slideI .i:nth-child(2){animation: bullet 16.4s ease 4100ms infinite} .slideI .i:nth-child(3){animation: bullet 16.4s ease 8200ms infinite} .slideI .i:nth-child(4){animation: bullet 16.4s ease 12300ms infinite} .slider{position:relative;width:400%; transition:all 800ms cubic-bezier(.770, 0.0, .175, 1.0);transition-timing-function:cubic-bezier(.770, 0.0, .175, 1.0); animation:slide 16.4s cubic-bezier(.770, 0.0, .175, 1.0) infinite} .slider >*{flex-shrink:0; width:calc(100% / 4)} .slider .item{position:relative;border-radius:var(--sliderBd-radius); overflow:hidden} .slider .img{display:block;padding-top:var(--sliderRatio); color:#d9e2f0;background-color:var(--contentBg-alt);background-position:center;background-size:cover;background-repeat:no-repeat} .slider .cap{display:block;position:absolute;left:0;bottom:0;right:0;padding:20px;padding-block-start:40px;background-image:linear-gradient(0deg, rgb(45 49 56 / 90%) 0%, rgb(45 49 56 / 50%) 60%, rgb(45 49 56 / 0%) 100%); font-family:var(--fontBody-alt)} 

/* Widget: FeaturedPost */ .itemP.featured article{--gap:20px; align-items:center;gap:var(--gap)} .itemP.featured article .pI{width:var(--thumbnailSize)} .itemP.featured article .pC{width:calc(100% - (var(--gap) + var(--thumbnailSize)))}

/* Widget: PopularPost */ .itemP.popular{--counter:30px; gap:18px;counter-reset:popular} .itemP.popular article.most{gap:18px} .itemP.popular .pH.info .label:not(:first-child)::before{content:'\00B7'; margin-inline:8px 6px} .itemP.popular .pT .name{font-size:var(--postTitle-fontItems)} .itemP.popular .pS{display:block} .itemP.popular .pS .snippet{-webkit-line-clamp:2} .itemP.popular article .pC::before{content:'0' counter(popular);counter-increment:popular; flex:0 0 var(--counter); color:var(--themeC-alt); font:700 1.1rem var(--fontBody-alt); opacity:.6} .itemP.popular article:not(:nth-child(-n+9)) .pC::before{content:counter(popular)} .itemP.popular article .pB{flex-grow:1; width:calc(100% - var(--counter))}

/* Widget: Label */ .itemL .labi:checked ~ label::before{content:attr(data-hide)} .itemL .labi:checked ~ label::after, .itemL .labi:not(:checked) ~ .lab >*:not(.s){display:none} .itemL .lab{--gap:10px; gap:var(--gap)} .itemL .lab >*{max-width:100%} .itemL .lab.list >*{width:calc((100% / 2) - (var(--gap) / 2))} .itemL .link{align-items:center;gap:8px; width:100%;padding:10px;border:1px solid var(--contentBg-sec);border-radius:var(--contentBd-radius);background-color:var(--contentBg-sec); line-height:18px} .itemL a.link:is(.c, .noBg){border-color:var(--contentBd-color)} .itemL .link:is(.c, .noBg){background-color:transparent} .itemL a.link:hover, .itemL div.link{border-color:var(--themeLink);box-shadow:0 0 0 .5px var(--themeLink) inset; filter:none} .itemL a.link:hover .count, .itemL div.link .count{color:var(--themeLink)} .itemL a.link:hover .count svg, .itemL div.link .count svg{stroke:none;fill:currentColor;opacity:1} .itemL .count.flexIn{gap:4px} .itemL .count::before{content:attr(data-text)} .itemL label{gap:6px; margin-top:10px;padding-block:8px} .itemL label::before{content:attr(data-show);color:var(--themeLink)} .itemL label::after{content:attr(data-length);font-size:smaller;opacity:.8}

/* Widget: RelatedPost */ .itemR{--cgap:20px;gap:30px var(--cgap)} .itemR article{--gap:20px; align-items:flex-start;gap:var(--gap)} .itemR .pI, .itemR .pC{width:100%} .itemR .pI .image{display:block;position:inherit; padding-top:var(--thumbnailRatio)} .itemR .pI .mi{position:absolute;top:0;left:0;bottom:0;right:0; background-position:center;background-size:cover;background-repeat:no-repeat} .itemR .pH.info .label:not(:first-child)::before{content:'\00B7'; margin-inline:8px} .itemR .pT .clamp{display:-webkit-box} .itemR .pS .snippet{-webkit-line-clamp:2} .itemR:not(.type-2, .type-3, .type-4){--colGap: 40px ; --thumbnailSize: 65px ; column-gap:var(--colGap)} .itemR:not(.type-2, .type-3, .type-4) >*{width:calc((100% / 2) - (var(--colGap) / 2))} .itemR:not(.type-2, .type-3, .type-4) article{flex-direction:row-reverse} .itemR:not(.type-2, .type-3, .type-4) .pC{width:calc(100% - (var(--gap) + var(--thumbnailSize)))} .itemR:not(.type-2, .type-3, .type-4) .pI{width:var(--thumbnailSize)} .itemR:not(.type-2, .type-3, .type-4) .pI .image{padding-top:var(--thumbnailRatio-box)} .itemR:is(.type-2, .type-3, .type-4) article{width:calc((100% / 3) - (var(--cgap) * 2/3))} .itemR:is(.type-2, .type-3, .type-4) .pT .name:not(.item){--postTitle-fontItems:1.1em}

/* Widget: ContactForm */ .formB{max-width:480px; font-size:1rem} .formB form{gap:20px} form .area{--paddingB:14px; --paddingI:16px; display:block;position:relative} form .area .n{display:block; position:absolute;top:var(--paddingB); padding-inline:6px;font-size:1rem;line-height:1.5; opacity:.8;transition:top var(--tDuration), padding var(--tDuration), var(--tShowHide), font-size var(--tDuration), background var(--tDuration)} .nB:not(.r) form .area .n{left:calc(var(--paddingI) - 6px)} .nB.r form .area .n{right:calc(var(--paddingI) - 6px)} form .area .sup{display:block; padding-inline:var(--paddingI);padding-block-start:4px;font-size:small;line-height:1.5} form input[type=email]:not([data-filled=true]):focus ~ .sup, form textarea:not([data-filled=true]):focus ~ .sup{color:#d32f2f} form input:is([type=text], [type=email]), form textarea{--themeLink:currentColor; display:block;width:100%; padding:var(--paddingB) var(--paddingI);border:var(--inputBd-line) solid var(--inputBd-color);border-radius:var(--inputBd-radius); color:var(--inputC);background-color:var(--themeBg); font:1rem/1.5 var(--fontBody); transition:border-color var(--tDuration), box-shadow var(--tDuration), min-height var(--tDuration)} form input:is([type=text][data-filled=true], [type=email][data-filled=true]), form textarea[data-filled=true], form input:is([type=text], [type=email]):focus, form textarea:focus{border-color:var(--themeLink);box-shadow:0 0 0 .5px var(--themeLink) inset} form input:is([type=text][data-filled=true], [type=email][data-filled=true]) ~ .n, form textarea[data-filled=true] ~ .n, form .area:focus-within .n{top:-10px;background-color:var(--themeBg);font-size:small; opacity:1} form textarea{min-height:100px} form textarea:focus, form textarea[data-filled=true]{min-height:200px}

/* Widget: ToC */ .tocP{position:fixed;top:var(--headerHeight); width:var(--tocWidth);height:calc(var(--vHeight) - var(--headerHeight)); margin-inline-end:var(--tocWidth-minus);color:var(--tocC);background-color:var(--tocBg); box-shadow:0 5px 30px 0 rgb(0 0 0 / 5%); opacity:0;visibility:hidden;transition:margin var(--tDuration), var(--tShowHide);z-index:5} .tocP:not(.r), .tocP.r::before{right:0} .tocP.r, .tocP:not(.r)::before{left:0} .tocP::before{content:''; position:absolute;top:0;bottom:0; border-inline-start:var(--tocBd-line) solid var(--tocBd-color); z-index:2} .tocIn{position:relative; height:100%; background-color:inherit} .tocIn label{align-items:center;gap:6px; position:absolute;top:0;left:0;right:0; height:60px;padding:10px 20px;background-color:inherit;z-index:1} .tocIn label::after{content:var(--tableToc)} .tocC{height:inherit; padding-block:60px var(--contentPadding-box);padding-inline:var(--contentPadding-box); line-height:1.3; overflow-x:hidden;overflow-y:scroll} .tocC a{/*display:-webkit-box;*/ display:inline; -webkit-line-clamp:3;-webkit-box-orient:vertical;overflow:hidden} .tocC ol{overflow:hidden} .tocC ol ol{margin-top:3px;padding-top:5px} .tocC ol ol ol ol{display:none} .tocC >ol >li:not(:last-child){margin-bottom:15px} .tocC li{position:relative;padding-inline-start:8px} .tocC li li{padding-inline-start:17px} .tocC li li:not(:last-child){margin-bottom:5px} .tocC li li::before{content:''; position:absolute;top:-389px; min-width:12px;height:400px;border:1.5px solid var(--themeBd-color);border-block-start:0;border-inline-end:0} .tocC:not(.r) li li::before{left:1px; border-radius:0 0 0 8px} .tocC.r li li::before{right:1px; border-radius:0 0 8px 0} .tocB span{position:fixed;top:calc(var(--headerHeight) + 40px); width:45px;height:40px; background-color:var(--tocBg); box-shadow:0 5px 20px 0 rgb(0 0 0 / 10%);opacity:0;visibility:hidden;transition:var(--tShowHide); z-index:1} .tocB:not(.r) span{right:0;border-radius:20px 0 0 20px} .tocB.r span{left:0;border-radius:0 20px 20px 0} .tocI:not(:checked) ~ .tocB span, .tocI:checked ~ .tocB.fc::after{opacity:1;visibility:visible} .tocI:checked ~ .tocP{margin-inline-end:0; opacity:1;visibility:visible}

/* Widget: Blog */ .blogP.flex{--gap:20px;gap:40px var(--gap)} .blogP.flex >article{gap:20px; width:calc((100% / 3) - (var(--gap) * 2/3))} .blogP.flex >article, .itemP.featured article{padding:var(--postPadding);border:var(--postBd-line) solid var(--postBd-color);border-radius:var(--postBd-radius); color:var(--postC);background-color:var(--postBg); box-shadow:0 8px 24px -4px var(--postBs-color); transition:box-shadow var(--tDuration); overflow:hidden} .blogP.flex >article:hover, .itemP.featured article:hover{box-shadow:0 20px 60px -20px var(--postBs-hoverColor)} .blogP.flex >article .pC, .itemP.featured article .pC{padding:var(--postPadding-content);padding-block-start:0} article.shop .prices{margin-block-start:.5em; line-height:1.2} article.shop .prices i{font-style:normal} article.shop .prices i.strike{opacity:.8; font-size:smaller} article.shop .prices i:not(.strike){display:block; color:var(--themeLink); font-weight:600;font-size:1.1em} article:not(.sponsor):hover .pF .jump{opacity:1}
/* Widget: Blog - title + breadcrumbs */ .blogT{align-items:baseline;justify-content:space-between; margin-bottom:var(--widgetTitle-space)} .blogT.home .title{margin:0} .blogT.item{justify-content:flex-start} .blogT.item .tab .n >*{overflow:hidden;text-overflow:ellipsis} .blogT.item .a::before{display:none} .blogT.item .tab:not(:first-child)::before, .blogT:not(.item) .n:not(.s)::before{content:var(--breadcrumbs); flex-shrink:0; margin-inline:8px} .blogT .tab{align-items:baseline; overflow:hidden} .blogT .a{flex-shrink:0; opacity:.8} .blogT .a::before{content:attr(data-text)} .blogT .n.name::after{content:attr(data-text); white-space:nowrap;overflow:hidden;text-overflow:ellipsis} .blogT .n.s{padding-inline-start:5px}
/* Widget: Blog - pagination */ .blogN, .blogPg{display:flex;flex-wrap:wrap;justify-content:flex-end;gap:10px; margin-block:calc(var(--contentSpace) * 1.5) 0} .blogN.n{justify-content:center} .blogN >*{font-size:inherit} .blogN >*::after{content:attr(data-text)} .blogN .m{cursor:not-allowed; color:var(--themeC-alt);background-color:var(--contentBg-sec)} .blogN .np{flex-direction:row-reverse} .blogN .np::after{content:var(--pageNext)} .blogN .pp{/*align-self:center;*/ margin-inline:-2px auto} .blogN .pp::after{content:var(--pagePrev)} .blogN .pp svg{width:14px;height:14px} .blogN svg.line{stroke-width:1.5} .blogN .j{margin-inline:auto} .blogN .j:not(.m){cursor:pointer} .blogN .j.n{background:transparent}
/* Widget: Blog - product */ .shop .pPad{margin-block:15px} .shop .pPric{display:flex;flex-direction:column; margin-block-start:30px;color:var(--themeLink);font-size:1.8rem} .shop .pPric i{font-style:normal} .shop .pPric .strike{order:2;color:var(--themeC); font-size:small;opacity:.8} .shop .pPric .price{font-weight:600;line-height:1.4} .shop .pPric::before{content:attr(data-text)} .shop .pPric::before, .shop .pInfo small{display:block;color:var(--themeC); font-size:small; opacity:.8} .shop .pInfo{font-size:1rem} .shop .pInfo:not(.o){--gap:20px; display:flex;gap:var(--gap)} .shop .pInfo:not(.o) >*{width:calc((100% / 2) - (var(--gap) / 2))} .shop .pMart{display:flex;flex-wrap:wrap;gap:8px 10px; margin-block:15px} .shop .pMart small{width:100%} .shop .pMart a{display:flex;align-items:center;justify-content:center; width:34px;height:34px;padding:4px;border:1px solid var(--contentBd-color);border-radius:12px;overflow:hidden}
/* Widget: Blog - post */ /* thumbnail and comment count */ .pI{position:relative; border-radius:var(--contentBd-radius);background-color:var(--contentBg-alt); overflow:hidden} .pI .thumbnail{display:block;position:inherit; padding-top:var(--thumbnailRatio)} .pI .thumbnail amp-img{position:absolute;top:50%;left:50%; min-width:100%;min-height:100%;max-height:100%; text-align:center;transform:translate(-50%, -50%)} .pI.youtube:not(.noImage) .thumbnail::after{content:''; display:flex;align-items:center;justify-content:center; position:absolute;top:0;left:0;right:0;bottom:0; background:rgb(0 0 0 / 30%) url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 512 512' fill='%23fffdfc'><path d='M133 440a35.37 35.37 0 01-17.5-4.67c-12-6.8-19.46-20-19.46-34.33V111c0-14.37 7.46-27.53 19.46-34.33a35.13 35.13 0 0135.77.45l247.85 148.36a36 36 0 010 61l-247.89 148.4A35.5 35.5 0 01133 440z'/></svg>") center / 24px no-repeat; opacity:0;transition:opacity var(--tDuration), -webkit-backdrop-filter var(--tDuration), backdrop-filter var(--tDuration); -webkit-backdrop-filter:saturate(180%) blur(10px); backdrop-filter:saturate(180%) blur(10px)} .pI.youtube:not(.noImage):hover .thumbnail::after{opacity:1} .pI.youtube img{max-width:100%;max-height:none} .pI .img{position:absolute;top:50%;left:50%; max-width:110%;max-height:100%; font-size:.7em;text-align:center; transform:translate(-50%, -50%)} .pI .img.null::before{content:var(--noImage)} .pI .bar{justify-content:flex-end;flex-direction:row-reverse;gap:6px; position:absolute;top:0; padding:8px; font-size:.76em} .pI .bar:not(.r){right:0} .pI .bar.r{left:0} .pI .bar >*{gap:3px; padding:4px 5px;border-radius:12px; color:#0e2045;background-color:#fffdfc; box-shadow:5px 5px 15px 0 rgb(0 0 0 / 10%)} .pI .bar >*:hover{filter:none} .pI .bar >*:not(.tag)::before{content:attr(data-text); text-indent:2px; opacity:.8} .pI .bar >.discount{background-color:#fff6bf} .pI .bar >.discount::before{opacity:1} /* head, time and label */ .time:not(.timeAgo)::before, .jump::before{content:attr(data-text)} .pH .reading::before{content:var(--readtimeBefore) ' '; margin-inline:5px} .pH .reading::after{content:' ' var(--readtimeAfter)} .pH.info{justify-content:flex-start;align-items:baseline; margin-block-end:8px} .pH.info .label::before{opacity:.8} .pH.info .label::before, .pH.info .label [data-text]::before{content:attr(data-text)} .pH.info .label >span:not(:first-child)::before{content:var(--breadcrumbs);opacity:.8} .pH.info .label [data-text]{display:inline;padding-block:4px} .pH.info .label a:hover{text-decoration:underline} .pH:not(.info){--gap:8px;--imgWidth:28px;--fontDate:inherit;--fontDate-phone:.93em; align-items:center;gap:var(--gap); margin-block:20px 25px} .pH:not(.info).tag{margin-block-start:25px} .pH:not(.info) .avatar.im{width:var(--imgWidth);height:var(--imgWidth)} .pH:not(.info) .m{display:inline-block;line-height:1.3} .pH:not(.info) .m::after{content:attr(data-text); margin-inline-end:5px} .pH:not(.info) .date{font-size:var(--fontDate); white-space:nowrap} .pH:not(.info) .time.update:not(.timeAgo)::before{content:var(--latestUpdate) ' ' attr(data-text)} .pH .item{width:calc(100% - (100px + var(--imgWidth)))} .pH .share{gap:10px; max-width:100px; margin-inline-start:auto; font-size:var(--fontDate)} .pH .share [aria-label=Share]{gap:7px; flex-direction:row-reverse} .pH .share [aria-label=Share]::before{content:attr(data-text)} /* title */ .pT .name{margin:0} .pT .name:not(.item){font:var(--postTitle-fontWg) var(--postTitle-fontItems)/1.3 var(--fontBody-alt);} .pT .item{font:var(--postTitle-fontWg) var(--postTitle-font)/1.3 var(--fontBody-alt)} .pT a:hover{text-decoration:underline} /* snippet */ .pS .snippet{margin-block:.75em .5em; line-height:1.5} .pS:not(.noImage) .snippet{display:-webkit-box} /* description */ .pD{margin-block:15px 25px; font:var(--postDescription-font)/1.4 var(--fontBody-alt)} /* foot */ .pF.items{gap:5px; margin-block-start:auto;padding-top:5px} .pF.items.shop{display:none} .pF.item{gap:var(--contentSpace); margin-top:var(--contentSpace)} .pF .jump{margin-inline-start:auto} .pF .jump:not(.sponsor){opacity:0; transition:var(--tShowHide)} .pF .jump:hover{text-decoration:underline} .pF .label{gap:10px} .pF .label >*::before{content:attr(aria-label)} .pF .label >*:hover{text-decoration:underline} .pF .labels .flex{gap:8px;flex-wrap:wrap;align-items:center} .pF .labels .flex >*{padding:8px 14px;border:1px solid var(--contentBd-color);border-radius:20px} .pF .labels .flex >*:not(label):hover{border-color:var(--themeLink);box-shadow:0 0 0 .5px var(--themeLink) inset} .pF .labels .flex >*:not(label)::before{content:attr(aria-label)} .pF .labels .li:not(:checked) ~ .flex >*:not(.s), .pF .labels .li:checked ~ .flex label{display:none} .pF .labels .flex label{padding-inline:0;border:0} .pF .labels .flex label::before{content:attr(data-show)} /* share */ .shared{position:fixed;left:0;right:0; z-index:10} .shareB .popIn{max-width:480px} .shareI{gap:30px} .shareL{display:grid;grid-template-columns:repeat(auto-fit, minmax(50px, 1fr));grid-auto-rows:50px;grid-gap:35px 15px; padding-bottom:30px} .shareL >[data-text]{position:relative} .shareL >[data-text]::after{content:attr(data-text);position:absolute; left:0;right:0;bottom:-18px; text-align:center;opacity:.8} .shareL >[data-text] >*{width:50px;height:50px;margin-inline:auto;border-radius:20px;background-color:var(--contentBg-alt);overflow:hidden} .shareC::before{content:var(--copyLink); opacity:.8} .shareC .copy{--gap:15px; align-items:center;gap:var(--gap); margin-top:15px;padding-inline:15px;border:1px solid var(--contentBd-color);border-radius:var(--contentBd-radius); overflow:hidden; transition:border var(--tDuration), background var(--tDuration), box-shadow var(--tDuration)} .shareC label{flex-shrink:0; padding:10px 0;color:var(--themeLink)} .shareC input{flex-grow:1; padding:16px 0;border:0;outline:0;background-color:transparent;opacity:.6} .shareC input:focus, .shareC .copy:hover input{opacity:1} /* writter */ .authors{gap:10px; padding-block:var(--contentPadding);border-block:1px solid var(--contentBd-color);background-color:var(--contentBg)} .authors .name{width:calc(100% - (40px + 14px));max-width:400px} .authors .m::before{content:attr(data-write) ' '; opacity:.8} .authors .m::after{content:attr(data-text); font-weight:500} .authors .d{margin-top:4px} .authors .namei:not(:checked) ~ .d label::before{content:attr(data-text); color:var(--themeLink)} .authors .namei:not(:checked) ~ .d .clamp{display:-webkit-box;-webkit-line-clamp:1} 
/* component */ .pE{position:relative;margin-top:40px; font:var(--postBody-font)/var(--lineHeight) var(--fontBody); transition:font var(--tDuration)} /* head */ .pE h1, .pE h2, .pE h3, .pE h4, .pE h5, .pE h6{margin-top:1em; line-height:1.3;font-family:var(--fontBody-alt)} .pE h1:target, .pE h2:target, .pE h3:target, .pE h4:target, .pE h5:target, .pE h6:target{margin-top:0;padding-top:var(--headerHeight)} .pE :is(h1, h2, h3, h4, h5, h6).h::before{content:attr(data-text)} /* Paragraph */ .pE p{margin-block:var(--lineSpacing)} .pRef{font:1rem/1.4 var(--fontBody-alt); opacity:.8;word-break:break-word} .pRef ol, .pRef ul{padding-inline-start:30px} .pIndent{text-indent:2.2em} .pE:not(.r) .dropCap{float:left;margin-block-start:5px;margin-inline-end:8px; font:3.4em/45px var(--fontBody-alt)} .pE hr{margin-block:var(--postBreak); border:0; font:24px var(--fontCode)} .pE hr::before{content:'\007E'; display:block; letter-spacing:.6em;text-indent:.6em;text-align:center; opacity:.8;clear:both} .pE hr.dot::before{content:'\2027 \2027 \2027'} .pE hr.line::before{content:'';border-bottom:1px solid var(--contentBd-color)} /* blockquote */ blockquote{position:relative; margin-inline:0;padding-block:8px;padding-inline-start:20px;border-inline-start:1px solid var(--contentBd-color); font-size:.97em;line-height:1.6; opacity:.8} blockquote.s-1, details.sp{padding-block:1.7em;padding-inline-start:40px; border-block:1px solid var(--contentBd-color);border-inline-start:0} blockquote.s-1::before{content:'\201D'; position:absolute;top:5px; font-size:60px;line-height:normal;opacity:.5} .pE:not(.r) blockquote.s-1::before{left:4px} .pE.r blockquote.s-1::before{right:4px}  /* img */ .pE img, .cm img{display:inline-block; border-radius:var(--postImageBd-radius)} /* scroll-img */ .psImg{--gap:14px; display:flex;flex-wrap:wrap;align-items:flex-start;justify-content:center;gap:var(--gap); margin-block:var(--lineSpacing)} .psImg img{display:block} .psImg >*{width:calc((100% / 2) - (var(--gap) / 2)); position:relative} .scImg >*{width:calc((100% / 3) - (var(--gap) * 2/3))} .btImg label{display:flex;align-items:center;justify-content:center; position:absolute;top:0;left:0;right:0;bottom:0; font-size:.93rem;font-family:var(--fontBody-alt); border-radius:var(--postImageBd-radius); color:#d9e2f0;background-color:var(--themeBg-pop); transition:var(--tShowHide); -webkit-backdrop-filter:saturate(180%) blur(10px); backdrop-filter:saturate(180%) blur(10px)} .hdImg .shImg{width:100%; margin-block:0} .inImg:not(:checked) ~ .hdImg .shImg{display:none} .inImg:checked ~ .hdImg .btImg label{opacity:0;visibility:hidden} /* caption */ figure{margin-inline:0} figcaption, .tr-caption, .psCaption{display:block;margin-top:8px; font-size:small;line-height:1.3; opacity:.8} /* ad */ .Blog ~ .LinkList{display:none} .pE .widget, .post .nAd >*{margin-block:40px} /* Note */ .note{position:relative; padding:18px 20px;padding-inline-start:40px;border-radius:var(--contentBd-radius); color:var(--noteC);background-color:var(--noteBg); font:14px/1.4 var(--fontBody-alt); overflow:hidden} .note::after{content:var(--noteAfter); position:absolute;top:12px; min-width:15px;text-align:center; font-size:1.5rem} .note.wr{color:var(--warnC);background-color:var(--warnBg)} .note.wr::after{content:var(--warnAfter)} .nB:not(.r) .note::after{left:14px} .nB.r .note::after{right:14px} /* list */ .step{counter-reset:num; line-height:1.6} .step li{position:relative;counter-increment:num; padding-inline-start:45px} .step li:not(:last-child){padding-bottom:15px} .step li::before{content:counter(num) '.'; display:flex;align-items:center;justify-content:center; position:absolute;top:0;width:30px;height:30px;border:1px solid var(--stepC);border-radius:50%; color:currentColor;font:small var(--fontBody-alt); transition:background var(--tDuration), color var(--tDuration)} .pE:not(.r) .step li::before{left:0} .pE.r .step li::before{right:0} .step li:hover::before{background-color:var(--stepC);color:var(--stepHover)} .step li::after{content:''; position:absolute;top:calc(30px + 8px);bottom:8px; border-inline-start:1px solid var(--stepC)} .pE:not(.r) .step li::after{left:calc(30px / 2)} .pE.r .step li::after{right:calc(30px / 2)} .step img{margin-top:1.2em} /* list - pros, cons */ .pros, .cons{margin-block:5px 15px;padding-inline-start:10px; font-size:1.02rem;line-height:1.5} .pros li, .cons li{margin-bottom:10px;padding-inline-start:10px} .pros li::marker{content:'\002B'} .cons li::marker{content:'\2212'} /* related */ .pRelate{margin-block:2.5em;padding-block:1.7em; border-block:var(--contentBd-line) solid var(--contentBd-color); font:14px/1.4 var(--fontBody-alt)} .pRelate b{font-weight:400; opacity:.8} .pRelate ul, .pRelate ol{margin-block:10px 0;padding-inline-start:20px} .pRelate li{padding-block:2px} .pRelate a:hover{text-decoration:underline} /* table */ .table{margin-block:1em;padding-block-end:4px; overflow-y:hidden;overflow-x:auto;scroll-behavior:smooth} table{margin-inline-end:auto; font:14px/1.4 var(--fontBody-alt)} table:not(.tr-caption-container){border:1px solid var(--contentBd-color);border-radius:var(--contentBd-radius); overflow:hidden} table:not(.tr-caption-container) td{padding:14px} table:not(.tr-caption-container) tr:not(:last-child) td, table th{border-bottom:1px solid var(--contentBd-color)} table th{padding:15px 14px; font-weight:500;text-align:inherit} table th:not(:last-child), table:not(.tr-caption-container) td:not(:last-child){border-inline-end:1px solid var(--contentBd-color)} .table.w90 table:not(.tr-caption-container){min-width:90%} .table.w100 table:not(.tr-caption-container){min-width:100%} .table.noLine table th:not(:last-child), .table.noLine table:not(.tr-caption-container) td:not(:last-child){border-inline-color:transparent} .table.withBg table:not(.tr-caption-container) tbody tr:nth-child(2n+1), .table.hoverBg table:not(.tr-caption-container) tbody tr:hover{background-color:var(--tableBg-color)} /* toc */ details.sp{padding:1.5em 1.25em;border-color:var(--themeLink);font-size:.96em} details.sp summary{display:flex;justify-content:space-between;align-items:baseline;column-gap:10px; line-height:1.4} details.sp summary::after{content:'\276F'; flex-shrink:0; color:var(--themeLink);font-size:small; transform:rotate(90deg);cursor:pointer} details.sp[open] summary::after{transform:rotate(-90deg)} details.toc .toC{margin-top:1em} details.toc a:hover{text-decoration:underline} details.toc a{/*display:-webkit-box;*/ display:inline; -webkit-line-clamp:3;-webkit-box-orient:vertical;overflow:hidden; color:inherit} details.toc ol{list-style:none;margin:0;padding:0; counter-reset:toc; overflow:hidden} details.toc ol ol{padding-top:5px} details.toc ol ol ol::before{content:''; position:absolute;top:0; width:15px;height:100%; border-inline-start:1.5px solid var(--contentBd-color)} details.toc ol ol ol ol{display:none} details.toc li{position:relative;padding-inline-start:28px} details.toc li::before{content:counters(toc,'.')'. ';counter-increment:toc; position:absolute;top:0; min-width:24px;font-size:small;line-height:1.8;text-align:end; opacity:.8} details.toc li li{padding-inline-start:17px} details.toc li li::before{content:''; top:-85px; min-width:12px;height:100px;border:1.5px solid var(--themeBd-color);border-block-start:0;border-inline-end:0;} .pE:not(.r) details.toc li::before{left:0; border-radius:0 0 0 8px} .pE.r details.toc li::before{right:0; border-radius:0 0 8px 0} .pE:not(.r) details.toc ol ol ol::before{left:0} .pE.r details.toc ol ol ol::before{right:0} /* accordion */ .showH{margin-block:1.7em; font:.98em/1.6 var(--fontBody)} details.ac{padding:1.5em 1.25em; border-bottom:var(--contentBd-line) solid var(--contentBd-color)} details.ac:first-child{border-top:var(--contentBd-line) solid var(--contentBd-color)} details.ac summary{display:flex;align-items:baseline;justify-content:space-between; transition:color var(--tDuration)} details.ac summary::after{content:'\276F'; flex-shrink:0;display:inline; font-size:small; transform:rotate(90deg);cursor:pointer} details.ac[open] summary{color:var(--themeLink)} details.ac:not(.alt)[open] summary::after{transform:rotate(-90deg)} details.ac.alt summary::after{content:'\002B'; font-size:1.25em;line-height:20px;transform:none} details.ac.alt[open] summary::after{content:'\2212'} details.ac .aC{margin-block:1em} details.ac .aC p:first-child{margin-block-start:0} /* youtube-fullpage */ .videoYt{position:relative; padding-bottom:56.25%; border-radius:var(--contentBd-radius);overflow:hidden} .videoYt iframe{position:absolute;width:100%;height:100%;left:0;right:0} /* youtube-lazy */ .lazyYt{position:relative;padding-top:56.25%;border-radius:var(--contentBd-radius); overflow:hidden} .lazyYt img{top:-16.84%;left:0; width:100%; border:0;border-radius:0;opacity:.95; z-index:-1} .lazyYt img:hover{transform:none;box-shadow:none} .lazyYt img, .lazyYt iframe, .lazyYt .play{position:absolute} .lazyYt iframe{bottom:0;right:0; width:100%;height:100%} .lazyYt .play{display:block;width:70px;height:70px; top:50%;left:50%; transform:translate3d(-50%,-50%,0); transition:all .5s ease} .lazyYt .play svg{width:inherit;height:inherit; fill:none;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:10;stroke-width:8} .lazyYt .play .c{stroke:rgba(255,255,255,.85);stroke-dasharray:650;stroke-dashoffset:650; transition:all .4s ease-in-out; opacity:.3} .lazyYt .play .t{stroke:rgba(255,255,255,.75);stroke-dasharray:240;stroke-dashoffset:480; transition:all .6s ease-in-out; transform:translateY(0)} .lazyYt .play:hover .t{animation:nudge .6s ease-in-out;-webkit-animation:nudge .6s ease-in-out} .lazyYt .play:hover .t, .lazyYt .play:hover .c{stroke-dashoffset:0; opacity:.9;stroke:var(--themeLink)} .nAMP .lazyYt{display:none} /* button */ .pE .button{margin-block:.4em} .pE .btnF .button{margin:0} /* button-download */ .dlBox{display:flex;align-items:center; max-width:500px; margin-block:1.6em;padding:.8em; border:1px solid var(--contentBd-color);border-radius:var(--contentBd-radius); font:14px var(--fontBody-alt); transition:box-shadow var(--tDuration), border-color var(--tDuration)} .dlBox:hover{box-shadow:0 15px 50px -20px rgb(0 0 0 / 20%)} .dlBox .fT{display:flex;align-items:center;justify-content:center;flex-shrink:0; width:42px;height:42px;background-color:rgb(152 155 159 / 20%);border-radius:var(--contentBd-radius)} .dlBox .fT::before{content:attr(data-text);opacity:.8} .dlBox .fT.lazy{background-size:cover;background-position:center;background-repeat:no-repeat} .dlBox .fT.lazy::before{display:none} .dlBox .button{flex-shrink:0;height:40px;margin:0;padding:10px 12px;font-size:small} .dlBox .button::after{content:attr(aria-label)} .dlBox .fN{flex-grow:1; width:calc(100% - 200px);padding:0 15px} .dlBox .fN >*{display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis} .dlBox .fS{line-height:1.5;font-size:small;opacity:.8} /* lightBox */ .lightBox{position:relative} .lightBox img{display:block; transition:position var(--tDuration), margin var(--tDuration)} .lightBox details .n, .lightBox details[open]{position:absolute;top:0;left:0;bottom:0;right:0; background-color:transparent; transition:position var(--tDuration), background-color var(--tDuration), backdrop-filter var(--tDuration), height var(--tDuration)} .lightBox details .n .c{position:fixed;bottom:-20px;right:-20px;width:42px;height:42px;border-radius:50%; color:currentColor;background-color:var(--contentBg); opacity:0;visibility:hidden;box-shadow:0 5px 20px -5px rgb(0 0 0 / 20%); transition:bottom var(--tDuration), right var(--tDuration), var(--tShowHide)} .lightBox details .n .c::after{content:'\2715'; font-weight:400;font-size:14px} .lightBox details[open]{position:fixed; height:var(--vHeight);background-color:var(--themeBg-pop);backdrop-filter:saturate(180%) blur(10px); z-index:10} .lightBox details[open] .n .c{bottom:20px;right:20px; opacity:1;visibility:visible} .lightBox details[open] ~ *, .lightBox details[open] ~ noscript >*{position:fixed;top:0;left:0;bottom:0;right:0;max-width:calc(100% - (var(--contentPadding) * 2));max-height:calc(100% - (var(--contentPadding) * 2));margin:auto; z-index:10} /* syntax */ .pre{color:var(--synC);background-color:var(--synBg);border:var(--synBd-line) solid var(--synBd-color);border-radius:var(--synBd-radius); direction:ltr} .pre:not(.tb){position:relative; margin:1.7em auto; font-family:var(--fontCode); overflow:hidden} .pre:not(.tb)::before{content:'</>'; display:flex;justify-content:flex-end; position:absolute;top:0;left:0;right:0; padding-inline:10px;color:var(--synGray);background-color:inherit; font-size:11px;line-height:30px; z-index:1; opacity:0;visibility:hidden} .pre:not(.tb).html::before{content:'.html'} .pre:not(.tb).css::before{content:'.css'} .pre:not(.tb).js::before{content:'.js'} .pre:not(.tb).custom::before{content:attr(data-text)} .pre:not(.tb, :hover)::before{opacity:1;visibility:visible; transition-delay: 2s} .pre:not(.tb) button{display:flex;justify-content:flex-end; position:absolute;top:0;right:0; padding:0 10px;border:0;color:var(--synGray);background-color:inherit; font-size:11px;line-height:30px; z-index:2} .pre:not(.tb, :hover) button{opacity:0;visibility:hidden; transition-delay: 2s; z-index:1} .pre pre, .pre.tb pre{margin:0;padding-top:30px; color:inherit;background-color:inherit} pre{display:block; position:relative; font:13px/1.6 var(--fontCode); color:var(--synC);background-color:var(--synBg); margin:1.7em auto;padding:20px;border-radius:var(--contentBd-radius); -moz-tab-size:2;tab-size:2;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none; overflow:auto;direction:ltr;white-space:pre} pre i{color:var(--synBlue);font-style:normal} pre i.block{color:#fff;background-color:var(--synBlue)} code, kbd{display:inline; padding:5px;border-radius:2px; font:14px var(--fontCode); background-color:#ebeced;color:#2f3337} /* Multi syntax */ .pre.tb .preH{font-size:.93rem; margin:0} .pre.tb .preH >*{padding-top:15px} .pre.tb .preH::after{content:'</>'; margin-left:auto;padding:15px; font:10px var(--fontCode); color:var(--synGray)} .pre.tb >:not(.preH){display:none} .pE input[id*="1"]:checked ~ div[class*="C-1"], .pE input[id*="2"]:checked ~ div[class*="C-2"], .pE input[id*="3"]:checked ~ div[class*="C-3"], .pE input[id*="4"]:checked ~ div[class*="C-4"]{display:block} /* hljs */ .hljs-comment, .hljs-code, .hljs-meta, pre i.gray{color:var(--synGray)} .hljs-name, .hljs-title, .hljs-bullet, .hljs-variable, .hljs-template-variable, .hljs-selector-id, .hljs-selector-class, .hljs-selector-tag, .hljs-literal, pre i.red{color:var(--synOrange)} .hljs-keyword, .hljs-string, .hljs-type, .hljs-section, .hljs-quote, .hljs-built_in, .hljs-builtin-name, pre i.blue{color:var(--synBlue)} .hljs-attribute{} .hljs-params, pre i.green{color:var(--synGreen)} .hljs-number, .hljs-symbol{color:var(--synRed)} .hljs-regexp, .hljs-link{color:var(--synGold)} .hljs-deletion{background-color:var(--warnBg);color:var(--warnC)} .hljs-addition{background-color:var(--noteBg);color:var(--noteC)} .hljs-strong{font-weight:bold} .hljs-code, .hljs-emphasis{font-style:italic} /* tabs */ .tbHd.stick:not(.preH){position:-webkit-sticky;position:sticky;top:var(--headerHeight);background-color:var(--contentBg); z-index:1} .tbHd{display:flex; margin-bottom:30px;border-bottom:var(--contentBd-line) solid var(--contentBd-color); font:14px/1.6 var(--fontBody-alt); overflow-x:scroll;overflow-y:hidden;scroll-behavior:smooth;scroll-snap-type:x mandatory; -ms-overflow-style:none;-webkit-overflow-scrolling:touch} .tbHd >*{position:relative; padding:12px 15px; transition:opacity var(--tDuration); opacity:.6;white-space:nowrap; scroll-snap-align:start} .tbHd >*::before{content:attr(data-text)} .tbHd >*::after{content:''; position:absolute;left:0;bottom:-1px;right:0; height:2px;border-radius:2px 2px 0 0;background-color:var(--themeLink); opacity:0; transition:var(--tShowHide)} .tbCn >*{display:none;width:100%} .tbCn >* p:first-child{margin-top:0} .pE input[id*="1"]:checked ~ .tbHd label[for*="1"], .pE input[id*="2"]:checked ~ .tbHd label[for*="2"], .pE input[id*="3"]:checked ~ .tbHd label[for*="3"], .pE input[id*="4"]:checked ~ .tbHd label[for*="4"]{color:var(--themeLink);opacity:1; font-weight:500} .pE input[id*="1"]:checked ~ .tbHd label[for*="1"]::after, .pE input[id*="2"]:checked ~ .tbHd label[for*="2"]::after, .pE input[id*="3"]:checked ~ .tbHd label[for*="3"]::after, .pE input[id*="4"]:checked ~ .tbHd label[for*="4"]::after{opacity:1} .pE input[id*="1"]:checked ~ .tbCn div[class*="Text-1"], .pE input[id*="2"]:checked ~ .tbCn div[class*="Text-2"], .pE input[id*="3"]:checked ~ .tbCn div[class*="Text-3"], .pE input[id*="4"]:checked ~ .tbCn div[class*="Text-4"]{display:block} /* split */ .blogPg{font-size:small; align-items:baseline;justify-content:center; gap:0} .blogPg >*:not(.page){display:inline-flex;align-items:center;justify-content:center;gap:8px; position:relative;min-width:40px;height:40px; border-radius:var(--contentBd-radius); color:inherit} .blogPg a{opacity:.6} .blogPg a:hover{opacity:1} .blogPg .current:not(.page)::after, .blogPg .n::after{content:'';display:block; width:20px;border-bottom:1px solid currentColor} .blogPg .n{gap:4px;margin-inline-start:5px; transition:gap var(--tDuration)} .blogPg .n::before{content:var(--pageNext)} .blogPg .n::after{width:1px; opacity:0;visibility:hidden;transition:width var(--tDuration), var(--tShowHide)} .blogPg .n:hover{gap:8px} .blogPg .n:hover::after{width:20px; opacity:1;visibility:visible} .blogPg .a:hover{color:var(--themeLink)} /* component: responsive */ @media screen and (max-width:640px){/* scroll-img */ .scImg{flex-wrap:nowrap;justify-content:flex-start; padding-inline:var(--contentPadding); overflow-y:hidden;overflow-x:scroll;scroll-behavior:smooth;scroll-snap-type:x mandatory; -ms-overflow-style:none;-webkit-overflow-scrolling:touch} .scImg >*{flex:0 0 80%;scroll-snap-align:center} .pE img.full{max-width:none;border-radius:0} /* Table */ .table{display:flex; padding-inline:var(--contentPadding)} /* full-width */ .pE img.full, .scImg, .table{position:relative;width:calc(100% + (var(--contentPadding) * 2)); margin-inline:var(--contentPadding-minus)} } @media screen and (max-width:500px){/* scroll-img */ .hdImg >*, .shImg >*, .grImg >*:first-child, .grImg >*:nth-child(4), .grImg >*:nth-child(7){width:100%} .pE .separator a{display:block!important; margin:0!important} /* button */ .btnF >*{flex-grow:1;justify-content:center} .btnF >*:first-child{flex:0 0 auto} .dlBox a::after{display:none} .dlBox .button{min-width:45px;height:45px;justify-content:center} }
/* comment */ .pR{margin-top:var(--contentSpace)} /* comment-button */ .cmButton .button{justify-content:center; width:100%;max-width:none;padding-block:18px;padding-inline:var(--contentPadding-box); font-family:var(--fontBody-alt)} .cmButton .button span::before{content:attr(data-comment)} .cmButton .button:hover{box-shadow:0 15px 50px -20px rgb(0 0 0 / 20%), 0 0 0 .5px var(--themeLink) inset} /* comment-head */ .cmH .s{gap:5px} .cmH .s::before{content:attr(data-text); opacity:.8} .cmi:checked ~ .cm .cmH .s::before{content:attr(data-new)} .cmi:checked ~ .cm .cmH .s svg{transform:rotate(180deg)} .cmi:checked ~ .cm .cmO{flex-direction:column-reverse} /* comment-func */ .item-control{display:none} #comment:target .cm.popUp{margin-bottom:0;opacity:1;visibility:visible} #comment:target .cm.popUp .fc::after{opacity:1;visibility:visible; background-color:var(--themeBg-pop); -webkit-backdrop-filter:saturate(180%) blur(10px); backdrop-filter:saturate(180%) blur(10px)} #comment:target .popI:not(:checked) ~ .cmButton, .popI:checked ~ .cmButton, #comment:not(:target) .popI:not(:checked) ~ .cmButton ~ .cm:not(.popUp){display:none} #comment:target .popI:checked ~ .cm.popUp{margin-bottom:-100%; opacity:0;visibility:hidden} #comment:target .popI:checked ~ .cm.popUp .fc::after{background-color:transparent; opacity:0;visibility:hidden; backdrop-filter:none} #comment:target .popI:checked ~ .cmButton{display:block} /* comment-title */ .cm .title{margin:0; font-size:1em} /* comment-iframe */ .cm.embed .cmF, .cmO .cmX{position:relative; width:calc(100% + (10px * 2));margin-inline:-10px} .cmm.note{margin-inline:10px;font-size:small} /* comment-list */ .cmO{margin-block-start:var(--contentPadding)} .cmO li{flex-wrap:wrap;gap:10px; padding-bottom:25px} .cmO li li{position:relative;padding-bottom:15px} .cmO .cmI{position:relative; width:calc(100% - (35px + 10px))} .cmT{width:100%} .cmT svg{color:var(--themeLink); margin-inline-start:3px} .cmT .time::before{content:'\00B7';margin-inline:8px} .cmC{color:var(--themeC-alt)} .cmC img{font-size:smaller;margin-block-start:1em} .cmC.delete{display:block;margin-block-start:.5em;padding:15px;border:1px dashed rgb(0 0 0 / 20%);border-radius:3px;text-align:center} .cmC i[rel=image]{display:block;position:relative;min-height:50px;margin-block-start:.5em; white-space:nowrap;overflow:hidden;text-overflow:ellipsis; font-size:.93em;opacity:.8} .cmC i[rel=image]::before{content:'Enable javascript to view image';display:flex;align-items:center;justify-content:center; position:absolute;top:0;left:0;bottom:0;right:0; padding:15px;border:1px dashed rgb(0 0 0 / 20%);border-radius:3px; background-color:var(--contentBg); text-align:center} .cmC i[rel=quote]{display:block;margin-block:1em .5em;padding-block:6px;padding-inline-start:15px;border-inline-start:1px solid var(--contentBd-color); opacity:.8} .cmC i[rel=pre]{display:block;margin-block:1em .5em;padding:15px;border:var(--synBd-line) solid var(--synBd-color);border-radius:var(--contentBd-radius); color:var(--synC);background-color:var(--synBg); font:normal 13px/1.6 var(--fontCode); -moz-tab-size:2;tab-size:2;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none; overflow:auto;direction:ltr;white-space:pre} .cmJ:not(.cmc), .cmR{margin-block-start:.75em} .cmJ:not(.cmc) >*::after{content:var(--reply)} .cmJ.cmc >*::after{content:var(--replies)} .cmR summary{align-items:center;padding-block:5px} .cmR summary::before{content:attr(aria-label)} .cmR summary::after{content:'';  display:var(--widgetTitle-afterD);vertical-align:middle; width:30px;margin-inline-start:8px;border-bottom:1px solid var(--widgetTitle-afterC)} .cmR[open] summary::before{content:attr(data-text)} .cmS{margin-block-start:1.5em} .cmS .cmI{width:100%} .cmS .cmA{position:absolute;width:20px} .cmS .cmA .avatar.im{min-width:20px;min-height:20px;max-width:20px;max-height:20px} .cmS .cmT{padding-inline-start:26px} .cmS .cmC{margin-block-start:.5em} 

/* Responsive */ 
@media screen and (max-width:1100px){/* mainC */ .mainB .blogB{width:calc(100% - ((var(--sidebarWidth) - 20px) + var(--contentSpace)))} .mainB .sideB{width:calc(var(--sidebarWidth) - 20px)} /* Widget: Blog */ .blogP.flex >article{width:calc((100% / 2) - (var(--gap) * 1/2))} }
@media screen and (min-width:897px){/* mainN */ .leftW{position:sticky;top:var(--headerHeight);height:calc(var(--vHeight) - var(--headerHeight))} .leftW::after{content:'';position:absolute;top:0;bottom:0;border-inline-end:var(--sideBd-line) solid var(--sideBd-color)} .leftW:not(.r)::after{right:0} .leftW.r::after{left:0} /* mainN: active and openMenu */ .nB:not(.openMenu) .navi:checked ~ .mainW .leftN, .nB.openMenu .navi:not(:checked) ~ .mainW .leftN{overflow-x:hidden;overflow-y:hidden} .nB:not(.openMenu) .navi:checked ~ .mainW .leftN:hover, .nB.openMenu .navi:not(:checked) ~ .mainW .leftN:hover{overflow-y:scroll} .nB.openMenu .mainN, .nB:not(.openMenu) .navi:checked ~ .mainW .mainN{--sideWidth-collapse: var(--sideWidth-expand)} .nB.openMenu .navi:checked ~ .mainW .mainN{--sideWidth-collapse: var(--sideWidth)} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav .n, .nB.openMenu .navi:checked ~ .mainW .leftNav .n{--top:6px;position:absolute;top:calc(var(--padding) - (var(--top) - 2px)); max-width:160px;padding:var(--top) 10px;border:var(--sideBd-line) solid var(--sideBd-color);border-radius:var(--contentBd-radiusA); background-color:var(--contentBg); box-shadow:0 10px 30px -5px rgb(0 0 0 / 10%); font-size:.93em; white-space:nowrap;overflow:hidden;text-overflow:ellipsis; z-index:1; opacity:0;visibility:hidden; transition:var(--tShowHide)} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav details .n, .nB.openMenu .navi:checked ~ .mainW .leftNav details .n{top:calc(var(--padding) - (var(--top) - 12px))} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav:not(.r) details .n, .nB.openMenu .navi:checked ~ .mainW .leftNav:not(.r) details .n{left:55px} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav.r details .n, .nB.openMenu .navi:checked ~ .mainW .leftNav.r details .n{right:55px} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav details .n li, .nB.openMenu .navi:checked ~ .mainW .leftNav details .n li{padding-inline-start:0} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav details .n li::after, .nB.openMenu .navi:checked ~ .mainW .leftNav details .n li::after, .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftN .profileIcon .n, .nB.openMenu .navi:checked ~ .mainW .leftN .profileIcon .n, .nB:not(.openMenu) .navi:checked ~ .mainW .leftN .profileIcon.team .avi, .nB.openMenu .navi:not(:checked) ~ .mainW .leftN .profileIcon.team .avi{display:none} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftN .profileIcon.team .avi, .nB.openMenu .navi:checked ~ .mainW .leftN .profileIcon.team .avi{display:flex} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav .a:hover .n, .nB.openMenu .navi:checked ~ .mainW .leftNav .a:hover .n, .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav details:hover .n, .nB.openMenu .navi:checked ~ .mainW .leftNav details:hover .n{opacity:1;visibility:visible} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav:not(.r) .n, .nB.openMenu .navi:checked ~ .mainW .leftNav:not(.r) .n{left:35px} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav.r .n, .nB.openMenu .navi:checked ~ .mainW .leftNav.r .n{right:35px} .nB:not(.openMenu) .navi:not(:checked) ~ .mainW .leftNav summary .flexIn, .nB.openMenu .navi:checked ~ .mainW .leftNav summary .flexIn{display:none} }
@media screen and (max-width:896px){/* mainH */ .nB:not(.headerSticky) .mainH{position:relative} /* mainN */ .mainR{width:100%} .mainL{position:fixed;top:0;bottom:0;width:calc(100% - (var(--contentPadding) * 2));max-width:var(--sideWidth-max); margin-inline-start:calc(-100% + (var(--contentPadding) * 2));margin-block:var(--sideMargin-phone); opacity:0;visibility:hidden; transition:margin var(--tDuration), var(--tShowHide); z-index:10; overflow:hidden} .mainL:not(.r){left:0} .mainL.r{right:0} .leftW{position:relative;height:calc(var(--vHeight) - (var(--sideMargin-phone) * 2)); border-radius:var(--sideBd-radiusTL) var(--sideBd-radiusTR) var(--sideBd-radiusBR) var(--sideBd-radiusBL); overflow:hidden} .leftN{overflow-y:scroll} .leftF{display:flex;align-items:center;justify-content:flex-end; position:absolute;left:0;bottom:0;right:0; height:var(--closeHeight-phone); border-block-start:var(--sideBd-line) solid var(--sideBd-color); background-color:inherit} .leftF label{align-items:inherit;justify-content:inherit; min-width:100px;padding-block:10px;color:var(--themeLink)} .leftF label, .leftP{background-color:transparent; z-index:1} .leftF label::before{content:var(--closeButton)} /* mainN: active */ .navi:checked ~ .mainW .mainL{opacity:1;visibility:visible; margin-inline-start:var(--sideMargin-phone);margin-inline-end:var(--sideMargin-phone)} .navi:checked ~ .mainW .fc[for=forNav]::after{opacity:1;visibility:visible; background-color:var(--themeBg-pop);backdrop-filter:saturate(180%) blur(10px); z-index:2} /* mainC */ .mainB{align-items:center;flex-direction:column; gap:calc(var(--contentSpace) * 1.5)} .mainB :is(.blogB, .sideB){flex:1 0 100%; width:100%} /* mainM/mainF */ .mainM{display:block} .mainM:not(.no-items) ~ .mainF{padding-block-end:calc(25px + var(--mobileHeight))} /* Widget: Sliders */ .slideB{width:calc(100% + (var(--contentPadding) * 2));margin-inline:var(--contentPadding-minus);padding-inline:calc(var(--contentPadding) / 2);border-radius:0} .slideI{margin-inline:calc(var(--contentPadding) / 2)} .slider{left:calc(var(--contentPadding-minus) / -2);right:calc(var(--contentPadding-minus) / -2)} .slider >*{padding-inline-end:var(--contentPadding)} /* Widget: Blog */ .blogP.flex >article{width:calc((100% / 3) - (var(--gap) * 2/3))} }
@media screen and (min-width:768px){/* Scrollbar custom */ ::-webkit-scrollbar{-webkit-appearance:none; width:4px;height:5px}::-webkit-scrollbar-track{background-color:transparent}::-webkit-scrollbar-thumb{background-color:rgb(0 0 0 / 15%); border-radius:10px}::-webkit-scrollbar-thumb:hover{background-color:rgb(0 0 0 / 35%)}::-webkit-scrollbar-thumb:active{background-color:rgb(0 0 0 / 35%)} }
@media screen and (min-width:641px){.mainB.full .sideB{display:none} }
@media screen and (max-width:640px){/* Variable */ .nB{--headerHeight:var(--headerHeight-phone); --postTitle-font:var(--postTitle-fontPhone); --thumbnailSize: 250px ;} /* Notify */ .nB:not(.r) .fixN, .nB.r .fixN{left:0;right:0} .nB .fixN{--minHeight:var(--minHeight-phone); margin-bottom:var(--contentPadding-minus); border-radius:0;box-shadow:none} /* noScript/cookie */ .nJ{bottom:0;max-width:none;margin-inline:0;border-radius:0;box-shadow:none} .nJ.cookie{margin-bottom:0} /* mainH */ .mainH{padding-inline:var(--contentPadding);border-radius:0 0 var(--headerBd-radiusBR) var(--headerBd-radiusBL)} .headL{--gap:12px; flex-grow:1; width:60%} .headR{flex-grow:0;gap:0; width:auto;margin-inline-start:auto;padding-inline:0} .headT{max-width:calc(100% - (var(--iconWidth) + var(--gap)) + 8px)} .headi.menu{margin-inline-start:-8px;padding-inline-start:0} .headi .sc{display:inline-flex} /* Widget: BlogSearch */ .BlogSearch{position:fixed;top:0;left:0;right:0; margin-block-start:var(--headerHeight-min); transition:margin var(--tDuration); z-index:2} .BlogSearch form{background-color:var(--headerBg);margin-inline:0;border-bottom:var(--headerBd-line) solid var(--headerBd-color);border-radius:0 0 var(--headerBd-radiusBR) var(--headerBd-radiusBL)} .BlogSearch input[type=search]{width:100%;height:var(--headerHeight);padding-inline:62px;border-width:0} .BlogSearch .b{padding-inline:var(--contentPadding)} .BlogSearch:focus-within{margin-block-start:0} .BlogSearch:focus-within input, .BlogSearch:hover input{background-color:inherit} /* Element: po-up */ .popUp{align-items:flex-end} .popUp .popIn{max-width:100%; margin-block-end:0; border:0;border-radius:var(--contentBd-radiusA) var(--contentBd-radiusA) 0 0} .popUp .popC{padding-block:0 calc(var(--closeHeight-phone) + var(--contentPadding-box))} .popUp .popH{position:static;padding:var(--contentPadding-box) 0} .popUp .popH::before{content:''; position:absolute;left:0;bottom:0;right:0; height:var(--closeHeight-phone); background-color:inherit;border-top:1px solid var(--contentBd-color); z-index:2} .popUp .popH .c{justify-content:flex-end; position:absolute;bottom:calc((var(--closeHeight-phone) - var(--iconWidth)) / 2); min-width:60px;width:auto; margin-inline-end:0;color:var(--themeLink);z-index:2} .popUp .popH .c::after{content:var(--closeButton)} .popUp .popH .c:not(.r){right:var(--contentPadding)} .popUp .popH .c.r{left:var(--contentPadding)} .popUp .popIn:not(.n){border-radius:0; height:var(--vHeight);max-height:100%} /* Widget: RelatedPost */ .itemR:not(.type-2, .type-3, .type-4) >*{width:100%;max-width:500px} .itemR:not(.type-2, .type-4) .pT .clamp{-webkit-line-clamp:2} .itemR:is(.type-2, .type-3, .type-4){--cgap:15px} .itemR:is(.type-2, .type-3, .type-4) article{--gap:15px;width:calc((100% / 2) - (var(--cgap) / 2))} .itemR:is(.type-2, .type-3, .type-4) .pT .name:not(.item){--postTitle-fontItems:1em} .itemR.type-4 .pS{display:block} /* Widget: ToC */ .tocP{top:var(--tocMargin);bottom:var(--tocMargin); height:auto; border-radius:var(--tocBd-radiusTL) var(--tocBd-radiusTR) var(--tocBd-radiusBR) var(--tocBd-radiusBL); overflow:hidden;z-index:11} .tocP:not(.r){right:var(--tocMargin)} .tocP.r{left:var(--tocMargin)} .tocB.fc::after{z-index:10} .tocP::before{display:none} .tocI:checked ~ .tocB.fc::after{background-color:var(--themeBg-pop);backdrop-filter:saturate(180%) blur(10px)} /* Widget: Blog */ .blogP.flex >article{width:calc((100% / 2) - (var(--gap) * 1/2))} .nB:not(.oneGrid) .blogP.flex >article{gap:15px} .nB:not(.oneGrid) .blogP.flex .pS .clamp{-webkit-line-clamp:2} /* Widget: Blog - post */ /* snippet and jumplink */ .pS:not(.show), .nB:not(.oneGrid) .pF .jump:not(.sponsor){display:none} }
@media screen and (max-width:500px){/* Variable */ .nB{--postPadding:var(--postPadding-phone); --postTitle-fontItems:var(--postTitle-fontItemsPhone); --postDescription-font:var(--postDescription-fontPhone); --postBody-font:var(--postBody-fontPhone); --thumbnailSize:100%} /* Widget: RelatedPost */ .itemR.type-3 article{flex-direction:row; width:100%} .itemR.type-3 .pI{--thumbnailSize:40%; width:var(--thumbnailSize)} .itemR.type-3 .pC{width:calc(100% - (var(--gap) + var(--thumbnailSize)))} .itemR.type-4{flex-wrap:nowrap; position:relative;width:calc(100% + (var(--contentPadding) *2)); margin-inline:var(--contentPadding-minus);padding-inline:var(--contentPadding); overflow-y:hidden;overflow-x:scroll; scroll-behavior:smooth;scroll-snap-type:x mandatory; -ms-overflow-style:none;-webkit-overflow-scrolling:none} .itemR.type-4 article{width:85%; scroll-snap-align:center} .itemR.type-4 .pT .name:not(.item){--postTitle-fontItems:1.1em} /* Widget: Blog */ .blogP.flex{--gap:15px} .oneGrid .blogP.flex >article{width:100%} /* head, time and label */ .pH:not(.info){--fontDate:var(--fontDate-phone)} .pH:not(.info) .date{display:block;overflow:hidden;text-overflow:ellipsis} .pH .share [aria-label=Share]:not(.nt)::before{display:none} }

/* Effect */ @keyframes nudge{ 0%{transform:translateX(0)} 30%{transform:translateX(-5px)} 50%{transform:translateX(5px)} 70%{transform:translateX(-2px)} 100%{transform:translateX(0)} } @keyframes slideIn{ 0%{opacity:0} 10%, 80%{opacity:1;bottom:var(--contentPadding)} 100%{bottom:calc(-100px + var(--contentPadding-minus)); opacity:0;visibility:hidden} } @keyframes slideTop{ 0%, 40%{opacity:0} 50%, 100%{opacity:1;bottom:0} } @keyframes bullet{ 1%, 21%{width:10px;background-color:var(--themeLink)} 22%, 39%{width:4px;background-color:rgb(0 0 0 / 15%)} } @keyframes slide{ 0%, 20%{margin-inline-start:0} 25%, 45%{margin-inline-start:-100%} 50%, 70%{margin-inline-start:-200%} 75%, 95%{margin-inline-start:-300%} }
/* Hide scroll */ .scrlH::-webkit-scrollbar{width:0;height:0} .scrlH::-webkit-scrollbar-track{background-color:transparent} .scrlH::-webkit-scrollbar-thumb{background-color:transparent;border:none}
/* Print (Do not print selected area) */ @media print{.noPrint{display:none}}
/* Do not copy */ /*body{user-select:none;-moz-user-select:none;-ms-user-select:none;-khtml-user-select:none;-webkit-user-select:none;-webkit-touch-callout:none} pre, code, kbd, i[rel=pre]{user-select:text;-moz-user-select:text;-ms-user-select:text;-khtml-user-select:text;-webkit-user-select:text;-webkit-touch-callout:text}*/

/* Set theme: switch */ .dc[aria-label=Dark] svg >*{display:none} .nB[data-theme=default] .inn .A, .nB[data-theme=dark] .inn .D, .nB[data-theme=light] .inn .L{color:var(--themeLink);opacity:1} .nB[data-theme=default] .inn .A .i, .nB[data-theme=dark] .inn .D .i, .nB[data-theme=light] .inn .L .i{box-shadow:0 0 0 1px var(--themeLink)} .nB[data-theme=default] .dc[aria-label=Dark] svg .sun, .nB[data-theme=light] .dc[aria-label=Dark] svg .sun, .nB[data-theme=dark] .dc[aria-label=Dark] svg .moon{display:block} .nB[data-theme=default] .dc[aria-label=Dark] svg{z-index:-1} .nB[data-theme=default] .dc[aria-label=Dark]{position:relative} .nB[data-theme=default] .dc[aria-label=Dark]::before{content:'A'; display:flex;align-items:center;justify-content:center; position:absolute;bottom:5px;right:4px; width:14px;height:16px;border-radius:6px;background-color:var(--headerBg); font-size:smaller} .nB[data-theme=default] .iSett .dc[aria-label=Dark]::before{background-color:var(--contentBg)} 
/* Set theme: dark */ .nB[data-theme=dark]{--themeLink: var(--darkLink); --themeC: var(--darkC); --themeC-alt: var(--darkC-alt); --themeBg: var(--darkBg); --themeBg-alt: var(--darkBg-alt); --themeBg-sec: var(--darkBg-sec); --themeBg-pop: var(--darkBg-pop); --themeBd-color: var(--darkBd-color); --synC: var(--themeC-alt); --synBg: var(--themeBg-alt); --synBd-color: var(--themeBd-color); --tableBg-color: rgb(45 49 56 / 80%); /* reset */ --buttonBg: var(--themeLink); --stepC: var(--themeLink); --headerBg: var(--themeBg); --sideBg: var(--themeBg); --sidebarBg: var(--themeBg); --footerBg: var(--themeBg); --postBg: var(--themeBg); --mobileBg: var(--themeBg-alt); --tocBg: var(--themeBg-alt); --contentBg: var(--themeBg); --contentBg-alt: var(--themeBg-alt); --contentBg-sec: var(--themeBg-sec); --buttonBd-color: var(--themeBd-color); --headerBd-color: var(--themeBd-color); --sideBd-color: var(--themeBd-color); --sidebarBd-color: var(--themeBd-color); --footerBd-color: var(--themeBd-color); --postBd-color: var(--themeBd-color); --mobileBd-color: var(--themeBd-color); --tocBd-color: var(--themeBd-color); --contentBd-color: var(--themeBd-color); --headerC: currentColor; --sideC: currentColor; --sidebarC: currentColor; --footerC: currentColor; --postC: currentColor; --mobileC: currentColor; --tocC: currentColor; --contentC: currentColor; } .nB[data-theme=dark] .ipopUp, .nB[data-theme=dark] .profilePop{background-color:var(--contentBg-alt)}
@media (prefers-color-scheme: dark){/* Set theme: switch */ .nB[data-theme=default] .dc[aria-label=Dark] svg .sun{display:none} .nB[data-theme=default] .dc[aria-label=Dark] svg .moon{display:block} .nB[data-theme=default]{--themeLink: var(--darkLink); --themeC: var(--darkC); --themeC-alt: var(--darkC-alt); --themeBg: var(--darkBg); --themeBg-alt: var(--darkBg-alt); --themeBg-sec: var(--darkBg-sec); --themeBg-pop: var(--darkBg-pop); --themeBd-color: var(--darkBd-color); --synC: var(--themeC-alt); --synBg: var(--themeBg-alt); --synBd-color: var(--themeBd-color); --tableBg-color: rgb(45 49 56 / 80%); /* reset */ --buttonBg: var(--themeLink); --stepC: var(--themeLink); --headerBg: var(--themeBg); --sideBg: var(--themeBg); --sidebarBg: var(--themeBg); --footerBg: var(--themeBg); --postBg: var(--themeBg); --mobileBg: var(--themeBg-alt); --tocBg: var(--themeBg-alt); --contentBg: var(--themeBg); --contentBg-alt: var(--themeBg-alt); --contentBg-sec: var(--themeBg-sec); --buttonBd-color: var(--themeBd-color); --headerBd-color: var(--themeBd-color); --sideBd-color: var(--themeBd-color); --sidebarBd-color: var(--themeBd-color); --footerBd-color: var(--themeBd-color); --postBd-color: var(--themeBd-color); --mobileBd-color: var(--themeBd-color); --tocBd-color: var(--themeBd-color); --contentBd-color: var(--themeBd-color); --headerC: currentColor; --sideC: currentColor; --sidebarC: currentColor; --footerC: currentColor; --postC: currentColor; --mobileC: currentColor; --tocC: currentColor; --contentC: currentColor; } .nB[data-theme=default] .ipopUp, .nB[data-theme=dark] .profilePop{background-color:var(--contentBg-alt)} }

/* Additional (Dummy ad) */ .adB{display:flex; min-height:60px;border:1px solid rgb(0 0 0 /10%);border-radius:2px;font-size:smaller} .adB::before{content:attr(data-text); margin:auto;opacity:.7}
/*]]>*/</style>
    
    <b:else/>
    <!--[ CSS for Blogger Layout ]-->
    <b:template-skin><![CDATA[
/* standard */ body#layout::before{content:'Median UI - By M R S K T .COM' ;position:absolute;top:10px;right:5px; font:.8rem Roboto, sans-serif; color:rgb(0 0 0 / 52%)} body#layout{width:1025px;margin:0 !important;padding:60px 0 0 !important;border:0 !important;text-align:left !important;position:relative} body#layout div.layout-widget-description{font-size:12px !important;line-height:16px !important} body#layout div.layout-title{font-size:15px !important} body#layout div.section{border-radius:2px} body#layout .section h4{font-size:15px !important; margin-left:0!important} body#layout .add_widget a{font-size:13px !important} body#layout .Blog .widget-content{height:auto !important}
/* custom */ body#layout .mainH, body#layout .headR, body#layout .mainN, body#layout .mainB{display:flex} body#layout .headL{width:30%} body#layout .headR{width:70%} body#layout .headR >*{width:50%} body#layout .mainL{width:25%} body#layout .mainR{width:75%} body#layout .blogB{width:60%} body#layout .sideB{width:40%} body#layout #HTML91 .widget-content, body#layout #HTML92 .widget-content, body#layout #HTML93 .widget-content, body#layout #HTML95 .widget-content, body#layout #HTML99 .widget-content{background-color:#f0f8ff !important}
/* notif */ body#layout #notif-widget{padding:0!important} body#layout #notif-widget .widget{margin-top:0!important} body#layout #notif-widget h4, body#layout #notif-widget .layout-widget-description{display:none !important}
]]></b:template-skin>
  </b:if>

  <b:defaultmarkups>
    <b:defaultmarkup type='Common'>
      <!--[ SVG icon lists ]-->
      
      <!--[ arrow-left by Iconsax ]-->
      <b:includable id='arrow-left-icon'>
        <svg class='line r' viewBox='0 0 24 24'><path d='M9.57 5.92993L3.5 11.9999L9.57 18.0699'/><path d='M20.5 12H3.67004'/></svg>
      </b:includable>
      
      <!--[ arrow-right by Iconsax ]-->
      <b:includable id='arrow-right-icon'>
        <svg class='line r' viewBox='0 0 24 24'><path d='M14.4301 5.92993L20.5001 11.9999L14.4301 18.0699'/><path d='M3.5 12H20.33'/></svg>
      </b:includable>
      
      <!--[ arrow-left-1 by Iconsax ]-->
      <b:includable id='arrow-left-1-icon'>
        <svg class='line r' viewBox='0 0 24 24'><path d='M15 19.9201L8.47997 13.4001C7.70997 12.6301 7.70997 11.3701 8.47997 10.6001L15 4.08008'/></svg>
      </b:includable>
      
      <!--[ arrow-right-1 by Iconsax ]-->
      <b:includable id='arrow-right-1-icon'>
        <svg class='line r' viewBox='0 0 24 24'><path d='M8.91003 19.9201L15.43 13.4001C16.2 12.6301 16.2 11.3701 15.43 10.6001L8.91003 4.08008'/></svg>
      </b:includable>
      
      <!--[ arrow-up-1 by Iconsax ]-->
      <b:includable id='arrow-up-1-icon'>
        <svg class='line r' viewBox='0 0 24 24'><path d='M19.9201 15.0499L13.4001 8.52989C12.6301 7.75989 11.3701 7.75989 10.6001 8.52989L4.08008 15.0499'/></svg>
      </b:includable>
      
      <!--[ arrow-down-1 by Iconsax ]-->
      <b:includable id='arrow-down-1-icon'>
        <svg class='line r' viewBox='0 0 24 24'><path d='M19.9201 8.94995L13.4001 15.47C12.6301 16.24 11.3701 16.24 10.6001 15.47L4.08008 8.94995'/></svg>
      </b:includable>
      
      <!--[ menu-2 by Feathericons ]-->
      <b:includable id='menu-2-icon'>
        <svg class='line' viewBox='0 0 24 24'><polyline points='2 17 7 12 2 7'/><line x1='8' x2='22' y1='5' y2='5'/><line x1='12' x2='22' y1='12' y2='12'/><line x1='8' x2='22' y1='19' y2='19'/></svg>
      </b:includable>
      
      <!--[ search by Iconsax ]-->
      <b:includable id='search-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M11.5 21C16.7467 21 21 16.7467 21 11.5C21 6.25329 16.7467 2 11.5 2C6.25329 2 2 6.25329 2 11.5C2 16.7467 6.25329 21 11.5 21Z'/><path d='M22 22L20 20'/></svg>
      </b:includable>
      
      <!--[ category-2 by Iconsax ]-->
      <b:includable id='category-2-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M17 10H19C21 10 22 9 22 7V5C22 3 21 2 19 2H17C15 2 14 3 14 5V7C14 9 15 10 17 10Z'/><path d='M5 22H7C9 22 10 21 10 19V17C10 15 9 14 7 14H5C3 14 2 15 2 17V19C2 21 3 22 5 22Z'/><path d='M6 10C8.20914 10 10 8.20914 10 6C10 3.79086 8.20914 2 6 2C3.79086 2 2 3.79086 2 6C2 8.20914 3.79086 10 6 10Z'/><path d='M18 22C20.2091 22 22 20.2091 22 18C22 15.7909 20.2091 14 18 14C15.7909 14 14 15.7909 14 18C14 20.2091 15.7909 22 18 22Z'/></svg>
      </b:includable>
      
      <!--[ frame by Iconsax ]-->
      <b:includable id='frame-icon'>
        <svg class='line' viewBox='0 0 24 24'><!--<path d='M9.25 9.05005C11.03 9.70005 12.97 9.70005 14.75 9.05005'/>--><path d='M16.8199 2H7.17995C5.04995 2 3.31995 3.74 3.31995 5.86V19.95C3.31995 21.75 4.60995 22.51 6.18995 21.64L11.0699 18.93C11.5899 18.64 12.4299 18.64 12.9399 18.93L17.8199 21.64C19.3999 22.52 20.6899 21.76 20.6899 19.95V5.86C20.6799 3.74 18.9499 2 16.8199 2Z'/></svg>
      </b:includable>
      
      <!--[ archive-add by Iconsax ]-->
      <b:includable id='archive-add-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M14.5 10.6499H9.5' stroke-miterlimit='10'/><path d='M12 8.20996V13.21' stroke-miterlimit='10'/><path d='M16.8199 2H7.17995C5.04995 2 3.31995 3.74 3.31995 5.86V19.95C3.31995 21.75 4.60995 22.51 6.18995 21.64L11.0699 18.93C11.5899 18.64 12.4299 18.64 12.9399 18.93L17.8199 21.64C19.3999 22.52 20.6899 21.76 20.6899 19.95V5.86C20.6799 3.74 18.9499 2 16.8199 2Z'/></svg>
      </b:includable>
      
      <!--[ archive-tick by Iconsax ]-->
      <b:includable id='archive-tick-icon'>
        <svg viewBox='0 0 24 24'><path d='M16.8203 1.91016H7.18031C5.06031 1.91016 3.32031 3.65016 3.32031 5.77016V19.8602C3.32031 21.6602 4.61031 22.4202 6.19031 21.5502L11.0703 18.8402C11.5903 18.5502 12.4303 18.5502 12.9403 18.8402L17.8203 21.5502C19.4003 22.4302 20.6903 21.6702 20.6903 19.8602V5.77016C20.6803 3.65016 18.9503 1.91016 16.8203 1.91016ZM15.6203 9.03016L11.6203 13.0302C11.4703 13.1802 11.2803 13.2502 11.0903 13.2502C10.9003 13.2502 10.7103 13.1802 10.5603 13.0302L9.06031 11.5302C8.77031 11.2402 8.77031 10.7602 9.06031 10.4702C9.35031 10.1802 9.83031 10.1802 10.1203 10.4702L11.0903 11.4402L14.5603 7.97016C14.8503 7.68016 15.3303 7.68016 15.6203 7.97016C15.9103 8.26016 15.9103 8.74016 15.6203 9.03016Z'/></svg>
      </b:includable>
      
      <!--[ bag by Iconsax ]-->
      <b:includable id='bag-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M7.5 7.67001V6.70001C7.5 4.45001 9.31 2.24001 11.56 2.03001C14.24 1.77001 16.5 3.88001 16.5 6.51001V7.89001'/><path d='M8.99999 22H15C19.02 22 19.74 20.39 19.95 18.43L20.7 12.43C20.97 9.99 20.27 8 16 8H7.99999C3.72999 8 3.02999 9.99 3.29999 12.43L4.04999 18.43C4.25999 20.39 4.97999 22 8.99999 22Z'/><path d='M15.4955 12H15.5045'/><path d='M8.49451 12H8.50349'/></svg>
      </b:includable>
      
      <!--[ tag by Iconsax ]-->
      <b:includable id='tag-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M4.16989 15.3L8.69989 19.83C10.5599 21.69 13.5799 21.69 15.4499 19.83L19.8399 15.44C21.6999 13.58 21.6999 10.56 19.8399 8.69005L15.2999 4.17005C14.3499 3.22005 13.0399 2.71005 11.6999 2.78005L6.69989 3.02005C4.69989 3.11005 3.10989 4.70005 3.00989 6.69005L2.76989 11.69C2.70989 13.04 3.21989 14.35 4.16989 15.3Z'/><path d='M9.5 12C10.8807 12 12 10.8807 12 9.5C12 8.11929 10.8807 7 9.5 7C8.11929 7 7 8.11929 7 9.5C7 10.8807 8.11929 12 9.5 12Z'/></svg>
      </b:includable>
      
      <!--[ tag-right by Iconsax ]-->
      <b:includable id='tag-right-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M4.21995 3.09998H15.6599C16.3399 3.09998 17.19 3.56998 17.55 4.14998L21.73 10.83C22.13 11.48 22.09 12.5 21.63 13.11L16.45 20.01C16.08 20.5 15.28 20.9 14.67 20.9H4.21995C2.46995 20.9 1.40999 18.98 2.32999 17.49L5.09995 13.06C5.46995 12.47 5.46995 11.51 5.09995 10.92L2.32999 6.48998C1.40999 5.01998 2.47995 3.09998 4.21995 3.09998Z'/></svg>
      </b:includable>
      
      <!--[ translate ]-->
      <b:includable id='translate-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M3 5H15M9 3V5M10.0482 14.5C8.52083 12.9178 7.28073 11.0565 6.41187 9M12.5 18H19.5M11 21L16 11L21 21M12.7511 5C11.7831 10.7702 8.06969 15.6095 3 18.129'/></svg>
      </b:includable>
      
      <!--[ moon and sun-2 (alternative) ]-->
      <b:includable id='moon-n-sun-2-icon'>
        <svg class='line' viewBox='0 0 24 24'>
          <g class='moon'><path d='M183.72453,170.371a10.4306,10.4306,0,0,1-.8987,3.793,11.19849,11.19849,0,0,1-5.73738,5.72881,10.43255,10.43255,0,0,1-3.77582.89138,1.99388,1.99388,0,0,0-1.52447,3.18176,10.82936,10.82936,0,1,0,15.118-15.11819A1.99364,1.99364,0,0,0,183.72453,170.371Z' transform='translate(-169.3959 -166.45548)'/></g>
          <g class='sun'><path d='M12 18.5C15.5899 18.5 18.5 15.5899 18.5 12C18.5 8.41015 15.5899 5.5 12 5.5C8.41015 5.5 5.5 8.41015 5.5 12C5.5 15.5899 8.41015 18.5 12 18.5Z'/><path d='M19.14 19.14L19.01 19.01M19.01 4.99L19.14 4.86L19.01 4.99ZM4.86 19.14L4.99 19.01L4.86 19.14ZM12 2.08V2V2.08ZM12 22V21.92V22ZM2.08 12H2H2.08ZM22 12H21.92H22ZM4.99 4.99L4.86 4.86L4.99 4.99Z' stroke-width='2'/></g>
        </svg>
      </b:includable>
      
      <!--[ profile-circle by Iconsax ]-->
      <b:includable id='profile-circle-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M12.12 12.78C12.05 12.77 11.96 12.77 11.88 12.78C10.12 12.72 8.71997 11.28 8.71997 9.50998C8.71997 7.69998 10.18 6.22998 12 6.22998C13.81 6.22998 15.28 7.69998 15.28 9.50998C15.27 11.28 13.88 12.72 12.12 12.78Z'/><path d='M18.74 19.3801C16.96 21.0101 14.6 22.0001 12 22.0001C9.40001 22.0001 7.04001 21.0101 5.26001 19.3801C5.36001 18.4401 5.96001 17.5201 7.03001 16.8001C9.77001 14.9801 14.25 14.9801 16.97 16.8001C18.04 17.5201 18.64 18.4401 18.74 19.3801Z'/><path d='M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z'/></svg>
      </b:includable>
      
      <!--[ user by Iconsax ]-->
      <b:includable id='user-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M12 12C14.7614 12 17 9.76142 17 7C17 4.23858 14.7614 2 12 2C9.23858 2 7 4.23858 7 7C7 9.76142 9.23858 12 12 12Z'/><path d='M20.5899 22C20.5899 18.13 16.7399 15 11.9999 15C7.25991 15 3.40991 18.13 3.40991 22'/></svg>
      </b:includable>
      
      <!--[ profile-2user by Iconsax ]-->
      <b:includable id='profile-2user-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M9.16006 10.87C9.06006 10.86 8.94006 10.86 8.83006 10.87C6.45006 10.79 4.56006 8.84 4.56006 6.44C4.56006 3.99 6.54006 2 9.00006 2C11.4501 2 13.4401 3.99 13.4401 6.44C13.4301 8.84 11.5401 10.79 9.16006 10.87Z'/><path d='M16.41 4C18.35 4 19.91 5.57 19.91 7.5C19.91 9.39 18.41 10.93 16.54 11C16.46 10.99 16.37 10.99 16.28 11'/><path d='M4.15997 14.56C1.73997 16.18 1.73997 18.82 4.15997 20.43C6.90997 22.27 11.42 22.27 14.17 20.43C16.59 18.81 16.59 16.17 14.17 14.56C11.43 12.73 6.91997 12.73 4.15997 14.56Z'/><path d='M18.3401 20C19.0601 19.85 19.7401 19.56 20.3001 19.13C21.8601 17.96 21.8601 16.03 20.3001 14.86C19.7501 14.44 19.0801 14.16 18.3701 14'/></svg>
      </b:includable>
      
      <!--[ home by Iconsax ]-->
      <b:includable id='home-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M12 18V15'/><path d='M10.07 2.81997L3.14002 8.36997C2.36002 8.98997 1.86002 10.3 2.03002 11.28L3.36002 19.24C3.60002 20.66 4.96002 21.81 6.40002 21.81H17.6C19.03 21.81 20.4 20.65 20.64 19.24L21.97 11.28C22.13 10.3 21.63 8.98997 20.86 8.36997L13.93 2.82997C12.86 1.96997 11.13 1.96997 10.07 2.81997Z'/></svg>
      </b:includable>
      
      <!--[ home-2 by Iconsax ]-->
      <b:includable id='home-2-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M9.02 2.84004L3.63 7.04004C2.73 7.74004 2 9.23004 2 10.36V17.77C2 20.09 3.89 21.99 6.21 21.99H17.79C20.11 21.99 22 20.09 22 17.78V10.5C22 9.29004 21.19 7.74004 20.2 7.05004L14.02 2.72004C12.62 1.74004 10.37 1.79004 9.02 2.84004Z'/><path d='M12 17.99V14.99'/></svg>
      </b:includable>
      
      <!--[ export by Iconsax ]-->
      <b:includable id='export-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M16.44 8.8999C20.04 9.2099 21.51 11.0599 21.51 15.1099V15.2399C21.51 19.7099 19.72 21.4999 15.25 21.4999H8.73998C4.26998 21.4999 2.47998 19.7099 2.47998 15.2399V15.1099C2.47998 11.0899 3.92998 9.2399 7.46998 8.9099'/><path d='M12 15.0001V3.62012'/><path d='M15.35 5.85L12 2.5L8.65002 5.85'/></svg>
      </b:includable>
      
      <!--[ share-icon by Feathericons ]-->
      <b:includable id='share-icon'>
        <svg class='line' viewBox='0 0 24 24'><circle cx='18' cy='5' r='3'/><circle cx='6' cy='12' r='3'/><circle cx='18' cy='19' r='3'/><line x1='8.59' x2='15.42' y1='13.51' y2='17.49'/><line x1='15.41' x2='8.59' y1='6.51' y2='10.49'/></svg>
      </b:includable>
      
      <!--[ message-text by Iconsax ]-->
      <b:includable id='message-text-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M8.5 19H8C4 19 2 18 2 13V8C2 4 4 2 8 2H16C20 2 22 4 22 8V13C22 17 20 19 16 19H15.5C15.19 19 14.89 19.15 14.7 19.4L13.2 21.4C12.54 22.28 11.46 22.28 10.8 21.4L9.3 19.4C9.14 19.18 8.77 19 8.5 19Z'/><path d='M7 8H17'/><path d='M7 13H13'/></svg>
      </b:includable>
      
      <!--[ info by Feathericons ]-->
      <b:includable id='info-icon'>
        <svg class='line' viewBox='0 0 24 24'><circle cx='12' cy='12' r='10'/><line x1='12' x2='12' y1='16' y2='12'/><line x1='12' x2='12.01' y1='8' y2='8'/></svg>
      </b:includable>
      
      <!--[ location by Iconsax ]-->
      <b:includable id='location-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M12 13.4299C13.7231 13.4299 15.12 12.0331 15.12 10.3099C15.12 8.58681 13.7231 7.18994 12 7.18994C10.2769 7.18994 8.88 8.58681 8.88 10.3099C8.88 12.0331 10.2769 13.4299 12 13.4299Z'/><path d='M3.62001 8.49C5.59001 -0.169998 18.42 -0.159997 20.38 8.5C21.53 13.58 18.37 17.88 15.6 20.54C13.59 22.48 10.41 22.48 8.39001 20.54C5.63001 17.88 2.47001 13.57 3.62001 8.49Z'/></svg>
      </b:includable>
      
      <!--[ chat-curver by Iconly ]-->
      <b:includable id='chat-icon'>
        <svg class='line' viewBox='0 0 24 24'><g transform='translate(2.000000, 2.000000)'><path d='M17.0710351,17.0698449 C14.0159481,20.1263505 9.48959549,20.7867004 5.78630747,19.074012 C5.23960769,18.8538953 1.70113357,19.8338667 0.933341969,19.0669763 C0.165550368,18.2990808 1.14639409,14.7601278 0.926307229,14.213354 C-0.787154393,10.5105699 -0.125888852,5.98259958 2.93020311,2.9270991 C6.83146881,-0.9756997 13.1697694,-0.9756997 17.0710351,2.9270991 C20.9803405,6.8359285 20.9723008,13.1680512 17.0710351,17.0698449 Z'/></g></svg>
      </b:includable>
      
      <!--[ folder-2 by Iconsax ]-->
      <b:includable id='folder-2-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M22 11V17C22 21 21 22 17 22H7C3 22 2 21 2 17V7C2 3 3 2 7 2H8.5C10 2 10.33 2.44 10.9 3.2L12.4 5.2C12.78 5.7 13 6 14 6H17C21 6 22 7 22 11Z'/><path d='M8 2H17C19 2 20 3 20 5V6.38'/></svg>
      </b:includable>
      
      <!--[ sms-edit by Iconsax ]-->
      <b:includable id='sms-edit-icon'>
        <svg class='line' viewBox='0 0 24 24'><path d='M12 20.5H7C4 20.5 2 19 2 15.5V8.5C2 5 4 3.5 7 3.5H17C20 3.5 22 5 22 8.5V11.5'/><path d='M17 9L13.87 11.5C12.84 12.32 11.15 12.32 10.12 11.5L7 9'/><path d='M19.21 14.77L15.6701 18.31C15.5301 18.45 15.4 18.71 15.37 18.9L15.18 20.25C15.11 20.74 15.45 21.0801 15.94 21.0101L17.29 20.82C17.48 20.79 17.75 20.66 17.88 20.52L21.4201 16.9801C22.0301 16.3701 22.3201 15.6601 21.4201 14.7601C20.5301 13.8701 19.82 14.16 19.21 14.77Z'/><path d='M18.7001 15.28C19.0001 16.36 19.8401 17.2 20.9201 17.5'/></svg>
      </b:includable>
      
      <!--[ play and pause by Ionicons ]-->
      <b:includable id='playPause-icon'>
        <svg viewBox='0 0 512 512'>
          <g class='play'><path d='M133 440a35.37 35.37 0 01-17.5-4.67c-12-6.8-19.46-20-19.46-34.33V111c0-14.37 7.46-27.53 19.46-34.33a35.13 35.13 0 0135.77.45l247.85 148.36a36 36 0 010 61l-247.89 148.4A35.5 35.5 0 01133 440z'/></g>
          <g class='pause'><path d='M208 432h-48a16 16 0 01-16-16V96a16 16 0 0116-16h48a16 16 0 0116 16v320a16 16 0 01-16 16zM352 432h-48a16 16 0 01-16-16V96a16 16 0 0116-16h48a16 16 0 0116 16v320a16 16 0 01-16 16z'/></g>
        </svg>
      </b:includable>
      
      <!--[ Document icon ]-->
      <b:includable id='document-icon'>
        <svg class='line' viewBox='0 0 24 24'><g transform='translate(3.610000, 2.750100)'><line x1='11.9858' x2='4.7658' y1='12.9463' y2='12.9463'/><line x1='11.9858' x2='4.7658' y1='9.1865' y2='9.1865'/><line x1='7.521' x2='4.766' y1='5.4272' y2='5.4272'/><path d='M7.63833441e-14,9.25 C7.63833441e-14,16.187 2.098,18.5 8.391,18.5 C14.685,18.5 16.782,16.187 16.782,9.25 C16.782,2.313 14.685,0 8.391,0 C2.098,0 7.63833441e-14,2.313 7.63833441e-14,9.25 Z'/></g></svg>
      </b:includable>
      
      <!--[ behance by DailyYouth ]-->
      <b:includable id='behance-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M13.09,15.65A5.49,5.49,0,0,0,9.5,6H3A1,1,0,0,0,2,7V25a1,1,0,0,0,1,1h7.5a5.5,5.5,0,0,0,2.59-10.35ZM4,8H9.5a3.5,3.5,0,0,1,0,7H4Zm6.5,16H4V17h6.5a3.5,3.5,0,0,1,0,7Z'/><path d='M23.5,13a6.5,6.5,0,0,0,0,13c4.05,0,5.33-2.26,5.38-2.35a1,1,0,0,0-.4-1.36,1,1,0,0,0-1.36.4S26.28,24,23.5,24a4.5,4.5,0,0,1-4.38-3.5H29a1,1,0,0,0,1-1A6.51,6.51,0,0,0,23.5,13Zm0,2a4.5,4.5,0,0,1,4.38,3.5H19.12A4.5,4.5,0,0,1,23.5,15Z'/><path d='M21,11h6a1,1,0,0,0,0-2H21a1,1,0,0,0,0,2Z'/></g></svg>
      </b:includable>
      
      <!--[ blogger by DailyYouth ]-->
      <b:includable id='blogger-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M24,3H8A5,5,0,0,0,3,8V24a5,5,0,0,0,5,5H24a5,5,0,0,0,5-5V8A5,5,0,0,0,24,3Zm3,21a3,3,0,0,1-3,3H8a3,3,0,0,1-3-3V8A3,3,0,0,1,8,5H24a3,3,0,0,1,3,3Z'/><path d='M22,15H20.44A3.91,3.91,0,0,0,21,13a4,4,0,0,0-4-4H13a4,4,0,0,0-4,4v6a4,4,0,0,0,4,4h6a4,4,0,0,0,4-4V16A1,1,0,0,0,22,15ZM11,13a2,2,0,0,1,2-2h4a2,2,0,0,1,0,4H11Zm10,6a2,2,0,0,1-2,2H13a2,2,0,0,1-2-2V17H21Z'/></g></svg>
      </b:includable>
      
      <!--[ dribbble by DailyYouth ]-->
      <b:includable id='dribbble-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M30,16A14,14,0,1,0,16,30a16,16,0,0,0,1.7-.11A1.09,1.09,0,0,0,18,30a1,1,0,0,0,.59-.21A14,14,0,0,0,30,16Zm-2.63,3.8a14,14,0,0,0-6.56-2.67,22.26,22.26,0,0,0-1-4.37,14,14,0,0,0,5.47-4.41A11.92,11.92,0,0,1,27.37,19.8ZM23.79,6.89a11.86,11.86,0,0,1-4.77,4,22,22,0,0,0-4.78-6.74A12.79,12.79,0,0,1,16,4,11.89,11.89,0,0,1,23.79,6.89ZM11.93,4.73l0,0a20,20,0,0,1,5.19,6.82A12.13,12.13,0,0,1,14,12,11.9,11.9,0,0,1,6.2,9.1,12,12,0,0,1,11.93,4.73ZM4,16a12,12,0,0,1,1.17-5.14A14,14,0,0,0,14,14a14,14,0,0,0,3.89-.55A19.5,19.5,0,0,1,18.77,17,14,14,0,0,0,7,23.86,11.89,11.89,0,0,1,4,16Zm4.44,9.31A12,12,0,0,1,19,19c0,.33,0,.67,0,1a19.68,19.68,0,0,1-1.64,7.92A12.12,12.12,0,0,1,16,28,11.94,11.94,0,0,1,8.44,25.31ZM19.72,27.4A21.73,21.73,0,0,0,21,20c0-.28,0-.55,0-.83a12,12,0,0,1,5.58,2.52A12.06,12.06,0,0,1,19.72,27.4Z'/></g></svg>
      </b:includable>
      
      <!--[ facebook by DailyYouth ]-->
      <b:includable id='facebook-i-icon'>
        <svg viewBox='0 0 32 32'><path d='M24,3H8A5,5,0,0,0,3,8V24a5,5,0,0,0,5,5H24a5,5,0,0,0,5-5V8A5,5,0,0,0,24,3Zm3,21a3,3,0,0,1-3,3H17V18h4a1,1,0,0,0,0-2H17V14a2,2,0,0,1,2-2h2a1,1,0,0,0,0-2H19a4,4,0,0,0-4,4v2H12a1,1,0,0,0,0,2h3v9H8a3,3,0,0,1-3-3V8A3,3,0,0,1,8,5H24a3,3,0,0,1,3,3Z'/></svg>
      </b:includable>
      
      <!--[ messenger by DailyYouth ]-->
      <b:includable id='messenger-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M16,2A13,13,0,0,0,8,25.23V29a1,1,0,0,0,.51.87A1,1,0,0,0,9,30a1,1,0,0,0,.51-.14l3.65-2.19A12.64,12.64,0,0,0,16,28,13,13,0,0,0,16,2Zm0,24a11.13,11.13,0,0,1-2.76-.36,1,1,0,0,0-.76.11L10,27.23v-2.5a1,1,0,0,0-.42-.81A11,11,0,1,1,16,26Z'/><path d='M21.4,13.2l-3.31,2.48-3.38-3.39a1,1,0,0,0-1.31-.09l-4,3a1,1,0,1,0,1.2,1.6l3.31-2.48,3.38,3.39a1,1,0,0,0,1.31.09l4-3a1,1,0,1,0-1.2-1.6Z'/></g></svg>
      </b:includable>
      
      <!--[ whatsapp by DailyYouth ]-->
      <b:includable id='whatsapp-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M16,2A13,13,0,0,0,8,25.23V29a1,1,0,0,0,.51.87A1,1,0,0,0,9,30a1,1,0,0,0,.51-.14l3.65-2.19A12.64,12.64,0,0,0,16,28,13,13,0,0,0,16,2Zm0,24a11.13,11.13,0,0,1-2.76-.36,1,1,0,0,0-.76.11L10,27.23v-2.5a1,1,0,0,0-.42-.81A11,11,0,1,1,16,26Z'/><path d='M19.86,15.18a1.9,1.9,0,0,0-2.64,0l-.09.09-1.4-1.4.09-.09a1.86,1.86,0,0,0,0-2.64L14.23,9.55a1.9,1.9,0,0,0-2.64,0l-.8.79a3.56,3.56,0,0,0-.5,3.76,10.64,10.64,0,0,0,2.62,4A8.7,8.7,0,0,0,18.56,21a2.92,2.92,0,0,0,2.1-.79l.79-.8a1.86,1.86,0,0,0,0-2.64Zm-.62,3.61c-.57.58-2.78,0-4.92-2.11a8.88,8.88,0,0,1-2.13-3.21c-.26-.79-.25-1.44,0-1.71l.7-.7,1.4,1.4-.7.7a1,1,0,0,0,0,1.41l2.82,2.82a1,1,0,0,0,1.41,0l.7-.7,1.4,1.4Z'/></g></svg>
      </b:includable>
      
      <!--[ youtube by DailyYouth ]-->
      <b:includable id='youtube-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M29.73,9.9A5,5,0,0,0,25.1,5.36a115.19,115.19,0,0,0-18.2,0A5,5,0,0,0,2.27,9.9a69,69,0,0,0,0,12.2A5,5,0,0,0,6.9,26.64c3,.24,6.06.36,9.1.36s6.08-.12,9.1-.36a5,5,0,0,0,4.63-4.54A69,69,0,0,0,29.73,9.9Zm-2,12A3,3,0,0,1,25,24.65a113.8,113.8,0,0,1-17.9,0,3,3,0,0,1-2.78-2.72,65.26,65.26,0,0,1,0-11.86A3,3,0,0,1,7.05,7.35C10,7.12,13,7,16,7s6,.12,9,.35a3,3,0,0,1,2.78,2.72A65.26,65.26,0,0,1,27.73,21.93Z'/><path d='M21.45,15.11l-8-4A1,1,0,0,0,12,12v8a1,1,0,0,0,.47.85A1,1,0,0,0,13,21a1,1,0,0,0,.45-.11l8-4a1,1,0,0,0,0-1.78ZM14,18.38V13.62L18.76,16Z'/></g></svg>
      </b:includable>
      
      <!--[ instagram by DailyYouth ]-->
      <b:includable id='instagram-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M22,3H10a7,7,0,0,0-7,7V22a7,7,0,0,0,7,7H22a7,7,0,0,0,7-7V10A7,7,0,0,0,22,3Zm5,19a5,5,0,0,1-5,5H10a5,5,0,0,1-5-5V10a5,5,0,0,1,5-5H22a5,5,0,0,1,5,5Z'/><path d='M16,9.5A6.5,6.5,0,1,0,22.5,16,6.51,6.51,0,0,0,16,9.5Zm0,11A4.5,4.5,0,1,1,20.5,16,4.51,4.51,0,0,1,16,20.5Z'/><circle cx='23' cy='9' r='1'/></g></svg>
      </b:includable>

      <!--[ twitter by DailyYouth ]-->
      <b:includable id='twitter-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M13.35,28A13.66,13.66,0,0,1,2.18,22.16a1,1,0,0,1,.69-1.56l2.84-.39A12,12,0,0,1,5.44,4.35a1,1,0,0,1,1.7.31,9.87,9.87,0,0,0,5.33,5.68,7.39,7.39,0,0,1,7.24-6.15,7.29,7.29,0,0,1,5.88,3H29a1,1,0,0,1,.9.56,1,1,0,0,1-.11,1.06L27,12.27c0,.14,0,.28-.05.41a12.46,12.46,0,0,1,.09,1.43A13.82,13.82,0,0,1,13.35,28ZM4.9,22.34A11.63,11.63,0,0,0,13.35,26,11.82,11.82,0,0,0,25.07,14.11,11.42,11.42,0,0,0,25,12.77a1.11,1.11,0,0,1,0-.26c0-.22.05-.43.06-.65a1,1,0,0,1,.22-.58l1.67-2.11H25.06a1,1,0,0,1-.85-.47,5.3,5.3,0,0,0-4.5-2.51,5.41,5.41,0,0,0-5.36,5.45,1.07,1.07,0,0,1-.4.83,1,1,0,0,1-.87.2A11.83,11.83,0,0,1,6,7,10,10,0,0,0,8.57,20.12a1,1,0,0,1,.37,1.05,1,1,0,0,1-.83.74Z'/></g></svg>
      </b:includable>

      <!--[ linkedin by DailyYouth ]-->
      <b:includable id='linkedin-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M24,3H8A5,5,0,0,0,3,8V24a5,5,0,0,0,5,5H24a5,5,0,0,0,5-5V8A5,5,0,0,0,24,3Zm3,21a3,3,0,0,1-3,3H8a3,3,0,0,1-3-3V8A3,3,0,0,1,8,5H24a3,3,0,0,1,3,3Z'/><path d='M11,14a1,1,0,0,0-1,1v6a1,1,0,0,0,2,0V15A1,1,0,0,0,11,14Z'/><path d='M19,13a4,4,0,0,0-4,4v4a1,1,0,0,0,2,0V17a2,2,0,0,1,4,0v4a1,1,0,0,0,2,0V17A4,4,0,0,0,19,13Z'/><circle cx='11' cy='11' r='1'/></g></svg>
      </b:includable>

      <!--[ tiktok by DailyYouth ]-->
      <b:includable id='tiktok-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M24,3H8A5,5,0,0,0,3,8V24a5,5,0,0,0,5,5H24a5,5,0,0,0,5-5V8A5,5,0,0,0,24,3Zm3,21a3,3,0,0,1-3,3H8a3,3,0,0,1-3-3V8A3,3,0,0,1,8,5H24a3,3,0,0,1,3,3Z'/><path d='M22,12a3,3,0,0,1-3-3,1,1,0,0,0-2,0V19a3,3,0,1,1-3-3,1,1,0,0,0,0-2,5,5,0,1,0,5,5V13a4.92,4.92,0,0,0,3,1,1,1,0,0,0,0-2Z'/></g></svg>
      </b:includable>

      <!--[ telegram by DailyYouth ]-->
      <b:includable id='telegram-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M24,28a1,1,0,0,1-.62-.22l-6.54-5.23a1.83,1.83,0,0,1-.13.16l-4,4a1,1,0,0,1-1.65-.36L8.2,18.72,2.55,15.89a1,1,0,0,1,.09-1.82l26-10a1,1,0,0,1,1,.17,1,1,0,0,1,.33,1l-5,22a1,1,0,0,1-.65.72A1,1,0,0,1,24,28Zm-8.43-9,7.81,6.25L27.61,6.61,5.47,15.12l4,2a1,1,0,0,1,.49.54l2.45,6.54,2.89-2.88-1.9-1.53A1,1,0,0,1,13,19a1,1,0,0,1,.35-.78l7-6a1,1,0,1,1,1.3,1.52Z'/></g></svg>
      </b:includable>

      <!--[ pinterest by DailyYouth ]-->
      <b:includable id='pinterest-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M16,2A14,14,0,1,0,30,16,14,14,0,0,0,16,2Zm0,26a12,12,0,0,1-3.81-.63l1.2-4.81A7.93,7.93,0,0,0,16,23a8.36,8.36,0,0,0,1.4-.12,8,8,0,1,0-9.27-6.49,1,1,0,0,0,2-.35,6,6,0,1,1,3.79,4.56L15,16.24A1,1,0,1,0,13,15.76l-2.7,10.81A12,12,0,1,1,16,28Z'/></g></svg>
      </b:includable>

      <!--[ tumblr by DailyYouth ]-->
      <b:includable id='tumblr-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M16,2A14,14,0,1,0,30,16,14,14,0,0,0,16,2Zm0,26A12,12,0,1,1,28,16,12,12,0,0,1,16,28Z'/><path d='M20,19a1,1,0,0,0-1,1,1,1,0,0,1-1,1H17a1,1,0,0,1-1-1V15h3a1,1,0,0,0,0-2H16V10a1,1,0,0,0-2,0v3H12a1,1,0,0,0,0,2h2v5a3,3,0,0,0,3,3h1a3,3,0,0,0,3-3A1,1,0,0,0,20,19Z'/></g></svg>
      </b:includable>

      <!--[ line by DailyYouth ]-->
      <b:includable id='line-i-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M16,2C8.28,2,2,7.38,2,14c0,5.48,4.34,10.24,10.44,11.6L12,28.87a1,1,0,0,0,.37.91A1,1,0,0,0,13,30a1,1,0,0,0,.35-.06C14,29.68,30,23.58,30,14,30,7.38,23.72,2,16,2ZM14.22,27.4l.33-2.47a1,1,0,0,0-.83-1.12C8.09,22.91,4,18.78,4,14,4,8.49,9.38,4,16,4S28,8.49,28,14C28,20.61,18.14,25.66,14.22,27.4Z'/><path d='M10,15.25H8.75V12a.75.75,0,0,0-1.5,0v4a.76.76,0,0,0,.75.75h2a.75.75,0,0,0,0-1.5Z'/><path d='M24,12.75a.75.75,0,0,0,0-1.5H22a.76.76,0,0,0-.75.75v4a.76.76,0,0,0,.75.75h2a.75.75,0,0,0,0-1.5H22.75v-.5H24a.75.75,0,0,0,0-1.5H22.75v-.5Z'/><path d='M13,11.25a.76.76,0,0,0-.75.75v4a.75.75,0,0,0,1.5,0V12A.76.76,0,0,0,13,11.25Z'/><path d='M19,11.25a.76.76,0,0,0-.75.75v1.75l-1.65-2.2a.75.75,0,0,0-1.35.45v4a.75.75,0,0,0,1.5,0V14.25l1.65,2.2a.75.75,0,0,0,.6.3.67.67,0,0,0,.24,0,.75.75,0,0,0,.51-.71V12A.76.76,0,0,0,19,11.25Z'/></g></svg>
      </b:includable>

      <!--[ github by Bombasticon ]-->
      <b:includable id='github-b-icon'>
        <svg viewBox='0 0 32 32'><g><path d='M16,3a13,13,0,0,0-3.46,25.53,1,1,0,1,0,.53-1.92,11,11,0,1,1,7-.4,15.85,15.85,0,0,0-.3-3.92A6.27,6.27,0,0,0,24.68,16a6.42,6.42,0,0,0-1.05-3.87,7.09,7.09,0,0,0-.4-3.36,1,1,0,0,0-1.1-.67,8,8,0,0,0-3.37,1.28A11.35,11.35,0,0,0,16,9a13.09,13.09,0,0,0-3,.43A5.74,5.74,0,0,0,9.62,8.25a1,1,0,0,0-1,.66,7.06,7.06,0,0,0-.37,3.19A7.15,7.15,0,0,0,7.2,16a6.66,6.66,0,0,0,5,6.28,7.43,7.43,0,0,0-.15.79c-1,.06-1.58-.55-2.32-1.48a3.45,3.45,0,0,0-1.94-1.53,1,1,0,0,0-1.15.76A1,1,0,0,0,7.35,22c.16,0,.55.52.77.81a4.74,4.74,0,0,0,3.75,2.25,4.83,4.83,0,0,0,1.3-.18h0a1,1,0,0,0,.29-.14l0,0a.72.72,0,0,0,.18-.21.34.34,0,0,0,.08-.09.85.85,0,0,0,.06-.17,1.52,1.52,0,0,0,.06-.2v0a4.11,4.11,0,0,1,.46-1.91,1,1,0,0,0-.76-1.65A4.6,4.6,0,0,1,9.2,16a4.84,4.84,0,0,1,.87-3,1,1,0,0,0,.24-.83,5,5,0,0,1,0-1.85,3.59,3.59,0,0,1,1.74.92,1,1,0,0,0,1,.23A12.49,12.49,0,0,1,16,11a9.91,9.91,0,0,1,2.65.43,1,1,0,0,0,1-.18,5,5,0,0,1,2-1,4.11,4.11,0,0,1,0,1.91,1.05,1.05,0,0,0,.32,1A4,4,0,0,1,22.68,16a4.29,4.29,0,0,1-4.41,4.46,1,1,0,0,0-.94.65,1,1,0,0,0,.28,1.11c.59.51.5,4,.47,5.36a1,1,0,0,0,.38.81,1,1,0,0,0,.62.21,1.07,1.07,0,0,0,.25,0A13,13,0,0,0,16,3Z'/></g></svg>
      </b:includable>
      
      <!--[ blank social ]-->
      <b:includable id='blank-s-icon'>
        <svg viewBox='0 0 32 32'><path d='M16,2A14,14,0,1,0,30,16,14,14,0,0,0,16,2Zm0,26A12,12,0,1,1,28,16,12,12,0,0,1,16,28Z'/><path d='M16,9.5A6.5,6.5,0,1,0,22.5,16,6.51,6.51,0,0,0,16,9.5Zm0,11A4.5,4.5,0,1,1,20.5,16,4.51,4.51,0,0,1,16,20.5Z'/></svg>
      </b:includable>
      
      <!--[ admin-icon ]-->
      <b:includable id='admin-icon'>
        <svg viewBox='0 0 24 24'><path d='M15.29,8.85l-4.73,4.74L8.71,11.73a1,1,0,0,0-1.42,1.42l2.56,2.56a1,1,0,0,0,1.42,0l5.44-5.44a1,1,0,1,0-1.42-1.42ZM12,2A10,10,0,0,0,2,12a9.89,9.89,0,0,0,2.26,6.33l-2,2a1,1,0,0,0-.21,1.09A1,1,0,0,0,3,22h9A10,10,0,0,0,12,2Zm0,18H5.41l.93-.93a1,1,0,0,0,0-1.41A8,8,0,1,1,12,20Z'/></svg>
      </b:includable>
      
      <!--[ Default markups (applies to all widgets) ]-->
      
      <!--[ Ad unit ]-->
      <b:includable id='defaultAdUnit'>
        <ins class='adsbygoogle' data-ad-format='auto' expr:data-ad-client='data:adClientId ?: data:blog.adsenseClientId' expr:data-ad-host='data:blog.adsenseHostId' expr:data-analytics-uacct='data:blog.analyticsAccountNumber' expr:style='data:style ?: &quot;display: block;&quot;'/>
        <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
      </b:includable>
      
      <!--[ In-feed ad ]-->
      <b:includable id='post-adI'>
        <div class='p nAd noPrint'>
          <b:comment>Paste your ad code right under this tag</b:comment>
          
        </div>
      </b:includable>
      
      <!--[ Before article ad ]-->
      <b:includable id='post-adT'>
        <div class='nAd noPrint'>
          <b:comment>Paste your ad code right under this tag</b:comment>
          
        </div>
      </b:includable>
      
      <!--[ After article ad ]-->
      <b:includable id='post-adB'>
        <div class='nAd noPrint'>
          <b:comment>Paste your ad code right under this tag</b:comment>
          
        </div>
      </b:includable>
      
      <!--[ related-ad ]-->
      <b:includable id='post-adRelate'>
        <div class='footerAd noPrint'>
          <b:comment>Paste your ad code right under this tag</b:comment>
          
          
        </div>
      </b:includable>
      
      <!--[ Widget blog title and breadcrumbs ]-->
      <b:includable id='titleAndBreadcrumbs'>
        <div class='blogT flex cInherit noPrint'>
          <b:class cond='data:view.isHomepage' name='home'/>
          <b:class cond='data:view.url != data:blog.homepageUrl.canonical path &quot;search&quot; and (data:view.search or data:view.isArchive)' name='search'/>
          <b:class cond='data:view.isSingleItem' name='item'/>
          
          <b:comment>Additional attributes of breadcrumbs</b:comment>
          <b:attr cond='data:view.isSingleItem' name='itemscope' value='itemscope'/>
          <b:attr cond='data:view.isSingleItem' name='itemtype' value='https://schema.org/BreadcrumbList'/>
          
          <b:if cond='data:view.isHomepage'>
            <h3 class='title'>
              <b:comment><!--[ Change <data:messages.latestPosts/> below to replace [Latest Posts] with your special text ]--></b:comment>
              All stories
            </h3>

            <b:elseif cond='data:view.isMultipleItems != data:view.isHomepage'/>
            <b:tag class='tab flexIn noWrap' name='div'>
              <b:if cond='data:view.search.query'>
                <span class='a flexIn fontM' expr:data-text='data:messages.search + &quot;:&quot;'/>
                <span class='n name s flexIn noWrap fontM' expr:data-text='data:view.search.query'/>
                
                <b:elseif cond='data:view.isArchive'/>
                <span class='a flexIn fontM' expr:data-text='data:messages.blogArchive + &quot;:&quot;'/>
                <span class='n name flexIn noWrap fontM' expr:data-text='data:blog.pageName'/>
                
                <b:else/>
                <a class='a flexIn fontM' expr:aria-label='data:messages.home' expr:data-text='data:messages.home' expr:href='data:blog.homepageUrl'/>
                <span class='n name flexIn ellips fontM'>
                  <b:if cond='data:view.search.label'>
                    <b:attr expr:value='data:blog.pageName' name='data-text'/>
                    <b:else/>
                    <b:comment><!--[ Change expr:value='data:messages.posts' below with value='your_text' to replace [Posts] with your special text ]--></b:comment>
                    <b:attr name='data-text' value='Stories'/>
                  </b:if>
                </span>
              </b:if>
            </b:tag>
            
            <b:elseif cond='data:view.isSingleItem'/>
            <b:include name='postBreadcrumbs'/>
          </b:if>
        </div>
      </b:includable>
      
      <!--[ Post breadcrumbs ]-->
      <b:includable id='postBreadcrumbs'>
        <b:loop index='b' values='data:posts' var='post'>
          <b:if cond='data:b == 0'>
            
            <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
              <b:tag class='tab flexIn shrink noWrap' itemprop='itemListElement' itemscope='itemscope' itemtype='https://schema.org/ListItem' name='div'>
                <a class='a flexIn fontM' expr:aria-label='data:messages.home' expr:data-text='data:messages.home' expr:href='data:blog.homepageUrl' itemprop='item'>
                  <span itemprop='name'><data:messages.home/></span>
                </a>
                <meta content='1' itemprop='position'/>
              </b:tag>
            </b:if>
            
            <b:if cond='data:post.labels'>
              <b:loop values='data:post.labels' var='label'>
                <b:if cond='data:label.name == &quot;Product&quot;'>
                  <b:tag class='tab flexIn shrink noWrap' itemprop='itemListElement' itemscope='itemscope' itemtype='https://schema.org/ListItem' name='div'>
                    <a class='n flexIn ellips fontM' expr:aria-label='data:label.name' expr:data-text='data:label.name' expr:href='data:label.url' itemprop='item'>
                      <span itemprop='name'><data:label.name/></span>
                    </a>
                    <meta content='2' itemprop='position'/>
                  </b:tag>
                </b:if>
              </b:loop>
              
              <b:loop index='i' values='data:post.labels' var='label'>
                <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot;, &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                  
                  <b:if cond='data:label.name != &quot;Product&quot; and data:label.name != &quot;Discount10&quot; and data:label.name != &quot;Discount20&quot; and data:label.name != &quot;Discount30&quot; and data:label.name != &quot;Discount40&quot; and data:label.name != &quot;Discount50&quot; and data:label.name != &quot;Discount60&quot; and data:label.name != &quot;Discount70&quot; and data:label.name != &quot;Discount80&quot; and data:label.name != &quot;Discount90&quot;'>
                    <b:if cond='data:i &lt;= 2'>
                      <b:tag class='tab flexIn shrink noWrap' itemprop='itemListElement' itemscope='itemscope' itemtype='https://schema.org/ListItem' name='div'>
                        <a class='n flexIn ellips fontM' expr:aria-label='data:label.name' expr:data-text='data:label.name' expr:href='data:label.url' itemprop='item'>
                          <span itemprop='name'><data:label.name/></span>
                        </a>
                        <meta content='3' itemprop='position'/>
                      </b:tag>
                    </b:if>
                  </b:if>
                  
                  <b:else/>
                  <b:comment>Replace the number 0 below with 1 or 2 to show more than 2 labels</b:comment>
                  <b:if cond='data:i &lt;= 0'>
                    <b:tag class='tab flexIn shrink noWrap' itemprop='itemListElement' itemscope='itemscope' itemtype='https://schema.org/ListItem' name='div'>
                      <a class='n flexIn ellips fontM' expr:aria-label='data:label.name' expr:data-text='data:label.name' expr:href='data:label.url' itemprop='item'>
                        <span itemprop='name'><b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='extL opacity'/><data:label.name/></span>
                      </a>
                      <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
                        <meta content='1' itemprop='position'/>
                        <b:else/>
                        <meta expr:content='data:i+2' itemprop='position'/>
                      </b:if>
                    </b:tag>
                  </b:if>
                  
                </b:if>
              </b:loop>
              
              <b:elseif cond='data:view.isPost'/>
              <div class='tab flexIn noWrap'>
                <span class='n name flexIn ellips fontM'>
                  <b:comment><!--[ Change expr:value='data:messages.posts' below with value='your_text' to replace [Posts] with your special text ]--></b:comment>
                  <b:attr expr:value='data:messages.posts' name='data-text'/>
                </span>
              </div>
            </b:if>
            
            <b:comment>Change data:view.isPage to data:view.isSingleItem if you want to show post title in breadcrumbs</b:comment>
            <b:if cond='data:view.isPage'>
              <div class='tab flexIn noWrap'>
                <span class='n name flexIn ellips fontM' expr:data-text='data:post.title'/>
              </div>
            </b:if>
          </b:if>
        </b:loop>
      </b:includable>
      
      <!--[ Post Thumbnail ]-->
      <b:includable id='postThumbnail'>
        <b:comment>If there is a youtube video in the post</b:comment>
        <b:if cond='data:post.featuredImage.isYoutube'>
          <b:if cond='!data:view.isPreview'>
            <img class='img lazy' expr:alt='data:post.title ? data:post.title : data:messages.image' expr:data-src='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 480, &quot;16:9&quot;) : data:post.featuredImage.youtubeMaxResDefaultUrl' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
            <b:else/>
            <img class='img' expr:alt='data:post.title ? data:post.title : data:messages.image' expr:src='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 480, &quot;16:9&quot;) : data:post.featuredImage.youtubeMaxResDefaultUrl'/>
          </b:if>
          <noscript><img class='img' expr:alt='data:post.title ? data:post.title : data:messages.image' expr:src='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 480, &quot;16:9&quot;) : data:post.featuredImage.youtubeMaxResDefaultUrl'/></noscript>
          <b:else/>
          
          <b:comment>Otherwise, the first picture will be taken</b:comment>
          <b:if cond='!data:view.isPreview'>
            <img class='img lazy' expr:alt='data:post.title ? data:post.title : data:messages.image' expr:data-src='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 480, &quot;16:9&quot;) : data:post.featuredImage' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
            <b:else/>
            <img class='img' expr:alt='data:post.title ? data:post.title : data:messages.image' expr:src='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 480, &quot;16:9&quot;) : data:post.featuredImage'/>
          </b:if>
          <noscript><img class='img' expr:alt='data:post.title ? data:post.title : data:messages.image' expr:src='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 480, &quot;16:9&quot;) : data:post.featuredImage'/></noscript>
        </b:if>
      </b:includable>
      
      <!--[ Post author image ]-->
      <b:includable id='postAuthorImage'>
        <b:if cond='data:post.author.authorPhoto.image'>
          <b:if cond='!data:view.isPost'>
            <div class='avatar im flex center bgAlt' expr:data-style='&quot;background-image: url(&quot; + resizeImage(data:post.author.authorPhoto.image,20,&quot;1:1&quot;) + &quot;)&quot;'>
              <b:class cond='!data:view.isPreview' name='lazy'/>
              <b:attr cond='data:view.isPreview' expr:value='&quot;background-image: url(&quot; + resizeImage(data:post.author.authorPhoto.image,20,&quot;1:1&quot;) + &quot;)&quot;' name='style'/>
            </div>
            <noscript><div class='avatar im flex center bgAlt' expr:style='&quot;background-image: url(&quot; + resizeImage(data:post.author.authorPhoto.image,20,&quot;1:1&quot;) + &quot;)&quot;'/></noscript>
            <b:else/>
            <div class='avatar im flex center bgAlt' expr:data-style='&quot;background-image: url(&quot; + resizeImage(data:post.author.authorPhoto.image,40,&quot;1:1&quot;) + &quot;)&quot;'>
              <b:class cond='!data:view.isPreview' name='lazy'/>
              <b:attr cond='data:view.isPreview' expr:value='&quot;background-image: url(&quot; + resizeImage(data:post.author.authorPhoto.image,20,&quot;1:1&quot;) + &quot;)&quot;' name='style'/>
            </div>
            <noscript><div class='avatar im flex center bgAlt' expr:style='&quot;background-image: url(&quot; + resizeImage(data:post.author.authorPhoto.image,40,&quot;1:1&quot;) + &quot;)&quot;'/></noscript>
          </b:if>
          <b:elseif cond='!data:view.isMultipleItems'/>
          <div class='avatar im flex center bgAlt'><b:include name='profile-circle-icon'/></div>
        </b:if>
      </b:includable>
      
      <!--[ Post author name ]-->
      <b:includable id='postAuthorName'>
        <span class='m' expr:data-text='data:post.author.name' expr:data-write='data:widgets.Blog.first.allBylineItems.author.label'/>
        
        <b:comment>Replace the code above with this if you want to add a custom link to the author name</b:comment>
        <!--<a class='m' expr:data-text='data:post.author.name' expr:data-write='data:widgets.Blog.first.allBylineItems.author.label'>
          <b:attr expr:value='data:post.author.name' name='aria-label'/>
          
          <b:comment>change # with your url</b:comment>
          <b:attr name='href' value='#'/>
          <b:attr name='rel' value='author noreferrer'/>
          <b:attr name='target' value='_blank'/>
        </a>-->
      </b:includable>
      
      <!--[ Post info ]-->
      <b:includable id='postInfo'>
        <b:if cond='data:widgets.Blog.first.allBylineItems.timestamp or data:widgets.Blog.first.allBylineItems.labels'>
          <b:tag class='pH info flex fontM' name='div'>
            
            <b:comment>Show label or Sponsored</b:comment>
            <b:include cond='data:post.labels' name='postLabels'/>
          </b:tag>
        </b:if>
      </b:includable>
      
      <!--[ Post timestamps ]-->
      <b:includable id='postTimestamps'>
        <b:if cond='data:widgets.Blog.first.allBylineItems.timestamp'>
          <time class='time ellips opacity' expr:data-text='format(data:post.date, &quot;MMM d, YYYY&quot;)' expr:datetime='data:post.date.iso8601' expr:title='&quot;Published on: &quot; + data:post.date format &quot;MMMM d, YYYY&quot;'>
            <b:class cond='data:post.lastUpdated == data:post.date' name='publish'/>
            <b:class cond='data:post.lastUpdated != data:post.date and (data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Update&quot; or data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Update and timeAgo&quot;)' name='update'/>
            <b:class cond='data:widget.type != &quot;PopularPosts&quot; and (data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;timeAgo&quot; or data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Update and timeAgo&quot;)' name='timeAgo noJava'/>
            <b:class cond='data:widget.type != &quot;PopularPosts&quot; and (data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Custom&quot;)' name='custom'/>
            <b:class cond='data:widget.type == &quot;PopularPosts&quot;' name='shrink'/>
            
            <b:if cond='data:widget.type != &quot;PopularPosts&quot;'>
              
              <b:comment>Update timestamp</b:comment>
              <b:if cond='data:post.lastUpdated != data:post.date and (data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Update&quot; or data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Update and timeAgo&quot;)'>
                <b:if cond='!data:view.isSingleItem'>
                  <b:attr expr:value='format(data:post.lastUpdated, &quot;MMM d, YYYY&quot;)' name='data-text'/>
                  <b:else/>
                  <b:attr expr:value='format(data:post.lastUpdated, &quot;MMMM d, YYYY&quot;)' name='data-text'/>
                </b:if>
                <b:attr expr:value='&quot;Updated on: &quot; + data:post.lastUpdated format &quot;MMMM d, YYYY&quot;' name='title'/>
                <b:attr expr:value='data:post.lastUpdated.iso8601' name='datetime'/>
              </b:if>
              
              <b:comment>Custom format</b:comment>
              <b:attr cond='data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Custom&quot;' expr:value='data:post.date' name='data-text'/>
              
              <b:else/>
              <b:if cond='data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Update&quot; or data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Update and timeAgo&quot;'>
                <b:attr expr:value='format(data:post.lastUpdated, &quot;MMM d&quot;)' name='data-text'/>
                <b:attr expr:value='&quot;Updated on: &quot; + data:post.lastUpdated format &quot;MMMM d, YYYY&quot;' name='title'/>
                <b:attr expr:value='data:post.lastUpdated.iso8601' name='datetime'/>
                <b:else/>
                <b:attr expr:value='format(data:post.date, &quot;MMM d&quot;)' name='data-text'/>
              </b:if>
            </b:if>
            
          </time>
        </b:if>
      </b:includable>
      
      <!--[ Post timeReading ]-->
      <b:includable id='postTimeread'>
        <bdi class='reading ellips opacity noJava' id='timeRead'/>
      </b:includable>
      
      <!--[ Post label ]-->
      <b:includable id='postLabel'>
        <div class='labels'>
          <b:tag class='li hidden' cond='data:post.labels.length &gt; (2 + 1)' id='forLabel' name='input' type='checkbox'/>
          
          <div class='flex fontSm cInherit'>
            <b:if cond='data:post.labels'>
              <b:loop index='i' values='data:post.labels' var='label'>
                <b:comment>Show only 3 labels</b:comment>
                <a expr:aria-label='data:label.name' expr:href='data:label.url' rel='tag'>
                  <b:class cond='data:i &lt;= 2' name='s'/>
                </a>
              </b:loop>
            </b:if>
            
            <b:tag aria-label='Show all labels' class='s' cond='data:post.labels.length &gt; (2 + 1)' expr:data-hide='data:messages.showLess' expr:data-show='&quot;+&quot; + (data:post.labels.length - (2 + 1)) + &quot; &quot; + data:messages.moreEllipsis' for='forLabel' name='label' role='button'/>
          </div>
        </div>
      </b:includable>
      
      <!--[ Share button ]-->
      <b:includable id='postShareButton'>
        <label aria-label='Share' class='flex center opacity i20' expr:data-text='data:messages.share' for='forShare'><b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot;, &quot;Sponsored&quot; ])' name='nt'/><b:include name='share-icon'/></label>
      </b:includable>
      
      <!--[ Share custom ]-->
      <b:includable id='postShare'>
        <div class='shared'>
          <input class='popI hidden' id='forShare' type='checkbox'/>
        
          <div class='shareB popUp'>
            <div class='popIn n'>
              <div class='popC'>
                <div class='popH flex'>
                  <span class='t' expr:data-text='data:messages.shareToOtherApps'/>
                  <label aria-label='Close' class='c' for='forShare'>
                    <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                  </label>
                </div>
              
                <div class='shareI flex column'>
                  <b:comment>Share link to other apps</b:comment>
                  <div class='shareL cInherit fontSm'>
                    <div data-text='Facebook'>
                      <a aria-label='Facebook' class='flex center op' expr:href='&quot;https://www.facebook.com/sharer.php?u=&quot; + data:blog.url.canonical' rel='noopener' role='button' target='_blank' title='Share on Facebook'>
                        <b:include name='facebook-i-icon'/>
                      </a>
                    </div>
                    <div data-text='Whatsapp'>
                      <a aria-label='Whatsapp' class='flex center op' expr:href='&quot;https://api.whatsapp.com/send?text=&quot; + data:blog.url.canonical' rel='noopener' role='button' target='_blank' title='Share on Whatsapp'>
                        <b:include name='whatsapp-i-icon'/>
                      </a>
                    </div>
                    <div data-text='Twitter'>
                      <a aria-label='Twitter' class='flex center op' expr:href='&quot;https://twitter.com/share?url=&quot; + data:blog.url.canonical' rel='noopener' role='button' target='_blank' title='Share on Twitter'>
                        <b:include name='twitter-i-icon'/>
                      </a>
                    </div>
                    <div data-text='Telegram'>
                      <a aria-label='Telegram' class='flex center op' expr:href='&quot;https://t.me/share/url?url=&quot; + data:blog.url.canonical' rel='noopener' target='_blank' title='Telegram'>
                        <b:include name='telegram-i-icon'/>
                      </a>
                    </div>
                    <div data-text='Pinterest'>
                      <a aria-label='Pinterest' class='flex center op' data-pin-config='beside' expr:href='&quot;https://pinterest.com/pin/create/button/?url=&quot; + data:blog.url.canonical + &quot;&amp;media=&quot; + resizeImage(data:blog.postImageUrl, 1600)' rel='noopener' target='_blank' title='Pinterest'>
                        <b:include name='pinterest-i-icon'/>
                      </a>
                    </div>
                    <div data-text='LinkedIn'>
                      <a aria-label='LinkedIn' class='flex center op' expr:href='&quot;https://www.linkedin.com/sharing/share-offsite/?url=&quot; + data:blog.url.canonical' rel='noopener' role='button' target='_blank' title='Share on LinkedIn'>
                        <b:include name='linkedin-i-icon'/>
                      </a>
                    </div>
                    <div data-text='Tumblr'>
                      <a aria-label='Tumblr' class='flex center op' data-text='Tumblr' expr:href='&quot;https://www.tumblr.com/share/link?url=&quot; + data:blog.url.canonical' rel='nofollow noreferrer' target='_blank' title='Tumblr'>
                        <b:include name='tumblr-i-icon'/>
                      </a>
                    </div>
                    <div data-text='Line'>
                      <a aria-label='Line' class='flex center op' expr:href='&quot;https://timeline.line.me/social-plugin/share?url=&quot; + data:blog.url.canonical' rel='noopener' target='_blank' title='Line'>
                        <b:include name='line-i-icon'/>
                      </a>
                    </div>
                    <div data-text='Email'>
                      <a aria-label='Email' class='flex center op' expr:href='&quot;mailto:?body=&quot; + data:blog.url.canonical' expr:title='data:messages.emailPost' target='_blank'>
                        <b:include name='sms-edit-icon'/>
                      </a>
                    </div>
                  </div>
                
                  <b:comment>Copy link to clipboard</b:comment>
                  <div class='shareC noJava' expr:data-text='data:messages.copyToClipboard'>
                    <div class='copy flex op i18'>
                      <b:comment>text input</b:comment>
                      <input expr:value='data:blog.url.canonical' id='getLink' onclick='this.select()' readonly='readonly'/>
                      <label aria-label='Copy link' for='getLink' onclick='copyLink()'><data:messages.copy/></label>
                    </div>
                  
                    <script>const dc = document, copyLink = () =&gt; { dc.getElementById(&quot;getLink&quot;).select(), dc.execCommand(&quot;copy&quot;), dc.getElementById(&quot;copied&quot;).innerHTML = &quot;<span class='fixN'><data:messages.linkCopiedToClipboard/></span>&quot; };</script>
                  </div>
                </div>
              </div>
            </div>
          
            <label class='fc' for='forShare'/>
          </div>
          
          <div class='noJava' id='copied'/>
        </div>
      </b:includable>
   
      <!--[ Comment button ]-->
      <b:includable id='commentButton'>
        <div class='cmButton'>
          <label class='button' for='forComments'>
            <b:comment>Delete tag bellow to change button style</b:comment>
            <b:class name='ln'/>
            
            <b:include name='chat-icon'/>
            <span expr:data-title='data:messages.comments'>
              <b:attr cond='data:post.numberOfComments &gt; 0' expr:value='data:messages.comments + &quot; (&quot; + data:post.numberOfComments + &quot;)&quot;' name='data-title'/>
              <b:if cond='data:post.numberOfComments &gt; 0'>
                <b:attr expr:value='data:messages.joinTheConversation + &quot; (&quot; + data:post.numberOfComments + &quot;)&quot;' name='data-comment'/>
                <b:else/>
                <b:attr expr:value='data:messages.postAComment' name='data-comment'/>
              </b:if>
            </span>
          </label>
        </div>
      </b:includable>
      
      <!--[ Comment count ]-->
      <b:includable id='commentCount'>
        <b:if cond='data:post.allowComments and data:post.numberOfComments &gt; 0'>
          <a class='flex center op i16' expr:aria-label='data:messages.comments' expr:data-text='data:post.numberOfComments' expr:href='data:post.url.canonical fragment &quot;comment&quot;' role='button'>
            <b:include name='chat-icon'/>
          </a>
        </b:if>
      </b:includable>
      
      <!--[ Comment iframe ]-->
      <b:includable id='commentIframe'>
        <b:include data='post' name='commentFormIframeSrc'/>
                        
        <iframe class='blogger-iframe-colorize blogger-comment-from-post lazy' expr:data-src='data:post.commentFormIframeSrc appendParams {skin: &quot;contempo&quot;}' id='comment-editor' name='comment-editor' title='Blogger comment'/>
                      
        <script src='https://www.blogger.com/static/v1/jsbin/157798655-comment_from_post_iframe.js'/>
        <script>BLOG_CMT_createIframe(&#39;<data:post.appRpcRelayPath/>&#39;);</script>
      </b:includable>
   
      <!--[ Comment Disqus ]-->
      <b:includable id='commentDisqus'>
        <div class='cmButton cmDisqus' id='disqus_thread'>
          <b:tag class='button' id='disqusshow' name='div' onclick='load_Comments()'>
            <b:comment>Delete tag bellow to change button style</b:comment>
            <b:class name='ln'/>
            
            <b:include name='chat-icon'/>
            <span><data:messages.joinTheConversation/></span>
          </b:tag>
        </div>
        
        <script>/*<![CDATA[*/ var disqus_shortname = "jagodesain"; !function(){var e=document.createElement("script");e.defer=!0,e.src="//"+disqus_shortname+".disqus.com/blogger_item.js",(document.getElementsByTagName("head")[0]||document.getElementsByTagName("body")[0]).appendChild(e)}(); function load_Comments(){var e=document.getElementById("disqusshow");e.style.display="none";var t="jagodesain";!function(){var e=document.createElement("script");e.defer=!0,e.src="https://"+t+".disqus.com/embed.js",(document.getElementsByTagName("head")[0]||document.getElementsByTagName("body")[0]).appendChild(e)}()}; var uri = window.location.toString(); /* to remove ?m=1 in mobile */ if (uri.indexOf("?m=1","?m=1") > 0) {var clean_uri = uri.substring(0, uri.indexOf("?m=1"));window.history.replaceState({}, document.title, clean_uri); }; /*]]>*/</script>
      </b:includable>
   
      <!--[ Comment Disqus on-scroll ]-->
      <b:includable id='commentDisqusScroll'>
        <div class='cmButton cmDisqus' id='disqus_thread'>
          <div id='disqus_empty'/>
        </div>
        
        <!--[ Disqus script by bungfrangki.com, change 'jagodesain' with your disqus_shortname ]-->
        <script>var disqus_blogger_current_url = &quot;<data:blog.canonicalUrl/>&quot;; if (!disqus_blogger_current_url.length) {disqus_blogger_current_url = &quot;<data:blog.url/>&quot;;} var disqus_blogger_homepage_url = &quot;<data:blog.canonicalHomepageUrl/>&quot;; var disqus_blogger_canonical_homepage_url = &quot;<data:blog.canonicalHomepageUrl/>&quot;;</script>
        <script>/*<![CDATA[*/ function load_disqus( disqus_shortname ) {var y = document.getElementById('disqus_empty'), t = document.getElementById('disqus_thread'), e = document.createElement('script'), d = document.createElement('script'), h = (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]); if( t && y ) {e.async = true; e.src = '//' + disqus_shortname + '.disqus.com/embed.js'; h.appendChild(e); d.async = !0; d.src = '//' + disqus_shortname + '.disqus.com/blogger_item.js'; h.appendChild(d); y.remove(); } }; window.addEventListener('scroll', function(e) {var currentScroll = document.scrollingElement.scrollTop; var t = document.getElementById('disqus_thread'); if( t && (currentScroll > t.getBoundingClientRect().top - 150) ) {load_disqus('jagodesain'); console.log('Disqus loaded.'); }}, false); var uri = window.location.toString(); /* to remove ?m=1 in mobile */ if (uri.indexOf("?m=1","?m=1") > 0) {var clean_uri = uri.substring(0, uri.indexOf("?m=1"));window.history.replaceState({}, document.title, clean_uri); }; /*]]>*/</script>
      </b:includable>
   
      <!--[ Comment FB ]-->
      <b:includable id='commentFB'>
        <div id='fb-root'/>
        <script src='http://connect.facebook.net/en_US/all.js#xfbml=1' type='deferjs'/>
        <div id='commentFB'><fb:comments expr:href='data:post.url' num_posts='10' width='650'/></div>
        <script>/*<![CDATA[*/ /* to remove ?m=1 in mobile */ var uri = window.location.toString(); if (uri.indexOf("?m=1","?m=1") > 0) {var clean_uri = uri.substring(0, uri.indexOf("?m=1"));window.history.replaceState({}, document.title, clean_uri); }; /*]]>*/</script>
      </b:includable>
      
      <!--[ Loadmore pagination ]-->
      <b:includable id='postPaginationMore'>
        <script> /*! Simple AJAX infinite scroll by Taufik Nurrohman dte.web.id */ !function(t,e){t.InfiniteScroll=function(n){function r(t,n){return n=n||e,n.querySelectorAll(t)}function o(t){return void 0!==t}function a(t){return&quot;function&quot;==typeof t}function i(t,e){t=t||{};for(var n in e)t[n]=&quot;object&quot;==typeof e[n]?i(t[n],e[n]):e[n];return t}function s(t,e,n){return o(t)?o(e)?void(o(n)?g[t][n]=e:g[t].push(e)):g[t]:g}function d(t,e){o(e)?delete g[t][e]:g[t]=[]}function l(t,e){if(o(g[t]))for(var n in g[t])g[t][n](e)}function c(){return L.innerHTML=p.text.loading,v=!0,M?(y.classList.add(p.state.loading),l(&quot;loading&quot;,[p]),void u(M,function(t,n){y.className=x+&quot; &quot;+p.state.load,h=e.createElement(&quot;div&quot;),h.innerHTML=t;var o=r(&quot;title&quot;,h),a=r(p.target.post,h),i=r(p.target.anchors+&quot; &quot;+p.target.anchor,h),s=r(p.target.post,H);if(o=o&amp;&amp;o[0]?o[0].innerHTML:&quot;&quot;,a.length&amp;&amp;s.length){var d=s[s.length-1];e.title=o,d.insertAdjacentHTML(&quot;afterend&quot;,&quot; &quot;),h=e.createElement(&quot;div&quot;);for(var c=0,u=a.length;u&gt;c;++c)h.appendChild(a[c]);d.insertAdjacentHTML(&quot;afterend&quot;,h.innerHTML),f(),M=i.length?i[0].href:!1,v=!1,q++,l(&quot;load&quot;,[p,t,n])}},function(t,e){y.classList.add(p.state.error),v=!1,f(1),l(&quot;error&quot;,[p,t,e])})):(y.classList.add(p.state.loaded),L.innerHTML=p.text.loaded,l(&quot;loaded&quot;,[p]))}function f(t){if(L.innerHTML=&quot;&quot;,T){h.innerHTML=p.text[t?&quot;error&quot;:&quot;load&quot;];var e=h.firstChild;e.onclick=function(){return 2===p.type&amp;&amp;(T=!1),c(),!1},L.appendChild(e)}}var u=&quot;infinite-scroll-state-&quot;,p={target:{posts:&quot;.posts&quot;,post:&quot;.post&quot;,anchors:&quot;.anchors&quot;,anchor:&quot;.anchor&quot;},text:{load:&quot;%s&quot;,loading:&quot;%s&quot;,loaded:&quot;%s&quot;,error:&quot;%s&quot;},state:{load:u+&quot;load&quot;,loading:u+&quot;loading&quot;,loaded:u+&quot;loaded&quot;,error:u+&quot;error&quot;}},g={load:[],loading:[],loaded:[],error:[]};p=i(p,n||{}),p.on=s,p.off=d;var h=null,u=function(e,n,r){if(t.XMLHttpRequest){var o=new XMLHttpRequest;o.onreadystatechange=function(){if(4===o.readyState){if(200!==o.status)return void(r&amp;&amp;a(r)&amp;&amp;r(o.responseText,o));n&amp;&amp;a(n)&amp;&amp;n(o.responseText,o)}},o.open(&quot;GET&quot;,e),o.send()}},T=1!==p.type,v=!1,H=r(p.target.posts)[0],L=r(p.target.anchors)[0],M=r(p.target.anchor,L),m=e.body,y=e.documentElement,x=y.className||&quot;&quot;,E=H.offsetTop+H.offsetHeight,j=t.innerHeight,A=0,b=null,q=1;if(M.length){M=M[0].href,H.insertAdjacentHTML(&quot;afterbegin&quot;,&quot; &quot;),h=e.createElement(&quot;div&quot;),f();var w=function(){E=H.offsetTop+H.offsetHeight,j=t.innerHeight,A=m.scrollTop||y.scrollTop,v||E&gt;A+j||c()};w(),0!==p.type&amp;&amp;t.addEventListener(&quot;scroll&quot;,function(){T||(b&amp;&amp;t.clearTimeout(b),b=t.setTimeout(w,200))},!1)}return p}}(window,document);
if(typeof InfiniteScroll !== &quot;undefined&quot;) { var infinite_scroll = new InfiniteScroll ({ type: 0,
target: { posts: &quot;.blogP&quot;, post: &quot;article.p&quot;, anchors: &quot;.blogN&quot;, anchor: &quot;.np&quot;},
text: {
load: &quot;<div class='j button' expr:aria-label='data:messages.loadMorePosts' expr:data-text='data:messages.loadMorePosts' role='button'/>&quot;,
loading: &quot;<div class='j m button' expr:data-text='data:messages.loading'><svg viewBox='0 0 50 50' x='0px' y='0px'><path d='M25.251,6.461c-10.318,0-18.683,8.365-18.683,18.683h4.068c0-8.071,6.543-14.615,14.615-14.615V6.461z'><animateTransform attributeName='transform' attributeType='xml' dur='0.6s' from='0 25 25' repeatCount='indefinite' to='360 25 25' type='rotate'/></path></svg></div>&quot;,
loaded: &quot;<div class='j m n button' expr:data-text='data:messages.noResultsFound'/>&quot;,
error: &quot;<div class='j e button' expr:aria-label='data:messages.loadMorePosts' expr:data-text='data:messages.moreEllipsis' role='button'/>&quot;} }); }</script>
      </b:includable>
        
      <!--[ All javascript ]-->
      <b:includable id='allJavascript'>
        <script>/*<![CDATA[*/ var _0x91f0=["\x73\x68\x69\x66\x74","\x70\x75\x73\x68","\x6F\x6D","\x6E\x42","\x32\x30\x70\x78\x3B\x20\x63\x6F\x6C\x6F","\x72\x3A\x23\x31\x34\x31\x37\x32\x30\x3B","\x66\x64\x66\x63\x3B\x20\x66\x6F\x6E\x74","\x6E\x4C\x20\x3E\x2A\x7B\x6D\x61\x72\x67","\x6F\x63\x6B\x3A\x34\x30\x70\x78\x7D\x20","\x36\x70\x78\x7D\x20\x2E\x69\x6E\x4C\x63","\x7D\x20\x2E\x69\x6E\x4C\x62\x7B\x74\x65","\x78\x74\x2D\x74\x72\x61\x6E\x73\x66\x6F","\x0A","\x6E\x4C\x2D\x63\x22\x3E\x0A\x20\x20\x20","\x6C\x6F\x63\x61\x74\x69\x6F\x6E","\x20\x6C\x65\x67\x61\x6C\x6C\x79\x20\x6F","\x72\x20\x63\x6F\x6E\x74\x61\x63\x74\x20","\x74\x68\x65\x20\x64\x65\x76\x65\x6C\x6F","\x63\x6C\x61\x73\x73\x3D\x22\x66\x6C\x65","\x22\x3E\x3A\x20\x4D\x65\x64\x69\x61\x6E","\x20\x20\x20\x3C\x61\x20\x63\x6C\x61\x73","\x2D\x6C\x61\x62\x65\x6C\x3D\x22\x43\x6F","\x6E\x74\x61\x63\x74\x20\x75\x73\x22\x20","\x20\x20\x20\x20\x20\x20\x3C\x73\x70\x61","\x20\x63\x6C\x61\x73\x73\x3D\x22\x6C\x69","\x68\x20\x64\x3D\x22\x4D\x31\x34\x2E\x34","\x33\x30\x31\x20\x35\x2E\x39\x32\x39\x39","\x33\x4C\x32\x30\x2E\x35\x30\x30\x31\x20","\x31\x31\x2E\x39\x39\x39\x39\x4C\x31\x34","\x2E\x34\x33\x30\x31\x20\x31\x38\x2E\x30","\x69\x6E\x74\x65\x72\x76\x61\x6C","\x65\x6E\x74","\x63\x72\x65\x61\x74\x65\x45\x6C\x65\x6D","\x69\x6E\x6E\x65\x72\x48\x54\x4D\x4C","","\x61\x70\x70\x65\x6E\x64","\x69\x76\x65\x21\x20\x42\x75\x79\x20\x74","\x6C\x65\x67\x61\x6C\x6C\x79\x20\x74\x6F","\x73\x2E\x20","\x59\x6F\x75\x72\x20\x64\x6F\x6D\x61\x69","\x6F\x75\x20\x66\x6F\x72\x20\x62\x75\x79","\x20\x53\x68\x61\x72\x65\x64\x20\x62\x79\x20\x68\x74\x74\x70\x73\x3A\x2F\x2F\x77\x77\x77\x2E\x6E\x6C\x64\x62\x6C\x6F\x67\x2E\x63\x6F\x6D","\x7C","\x64\x61\x74\x61\x62\x61\x73\x65\x4A\x73\x6F\x6E","\x30","\x31","\x32","\x69\x64","\x33","\x73\x72\x63","\x34","\x2F\x2F","\x63\x6B\x3D","\x31\x32\x7C\x31\x7C\x30\x7C\x39\x7C\x38","\x35","\x63\x61\x6C\x6C\x62\x61\x63\x6B\x3D","\x73\x70\x6C\x69\x74","\x58\x55\x56\x4C\x59","\x24\x74","\x24\x74\x6F\x74\x61\x6C\x52\x65\x73\x75","\x36","\x37","\x38","\x39","\x62\x42\x77\x62\x45","\x31\x30","\x31\x31","\x66\x65\x65\x64","\x31\x32","\x65\x6E\x74\x72\x79","\x75\x66\x6E\x63\x4E","\x31\x33","\x6E\x4A\x73","\x6D\x65","\x2E\x77\x69\x64\x67\x65\x74\x20\x69\x6E","\x70\x75\x74\x5B\x74\x79\x70\x65\x3D\x73","\x65\x61\x72\x63\x68\x5D\x2C\x20\x2E\x77","\x70\x65\x3D\x65\x6D\x61\x69\x6C\x5D\x2C","\x20\x2E\x77\x69\x64\x67\x65\x74\x20\x74","\x6C\x65\x6E\x67\x74\x68","\x69\x6E\x70\x75\x74","\x4D\x46\x43\x59\x41","\x76\x61\x6C\x75\x65","\x64\x61\x74\x61\x2D\x66\x69\x6C\x6C\x65\x64","\x74\x65","\x4F\x72\x64\x72\x52","\x2E\x6D\x61\x69\x6E\x48","\x73","\x48\x77\x6A\x58\x59","\x69\x66\x72\x61\x6D\x65","\x45\x50\x6C\x57\x77","\x72","\x77\x2E\x79\x6F\x75\x74\x75\x62\x65\x2E","\x2E\x6C\x61\x7A\x79\x59\x74","\x4A\x6B\x6D\x52\x53","\x61\x6C\x74","\x64\x61\x74\x61\x2D\x73\x72\x63","\x73\x65\x74\x41\x74\x74\x72\x69\x62\x75","\x66\x76\x6F\x6C\x6D","\x64","\x64\x61\x74\x61\x3A\x69\x6D\x61\x67\x65\x2F\x70\x6E\x67\x3B\x62\x61\x73\x65\x36\x34\x2C\x52\x30\x6C\x47\x4F\x44\x6C\x68\x41\x51\x41\x42\x41\x41\x44\x2F\x41\x43\x77\x41\x41\x41\x41\x41\x41\x51\x41\x42\x41\x41\x41\x43\x41\x44\x73\x3D","\x68\x74\x74\x70\x73\x3A\x2F\x2F\x69\x6D","\x64\x61\x74\x61\x73\x65\x74","\x3F\x72\x65\x6C\x3D\x30\x26\x73\x68\x6F","\x77\x69\x6E\x66\x6F\x3D\x30\x26\x61\x75","\x63\x62\x46\x53\x44","\x61\x64\x64\x45\x76\x65\x6E\x74\x4C\x69","\x73\x74\x65\x6E\x65\x72","\x72\x6F\x6F\x74\x4D\x61\x72\x67\x69\x6E","\x31\x70\x78","\x6C\x6F\x61\x64","\x6F\x6E","\x2E\x6E\x42","\x71\x75\x65\x72\x79\x53\x65\x6C\x65\x63","\x69\x6E\x6E\x65\x72\x48\x65\x69\x67\x68","\x74","\x70\x78","\x79","\x72\x65\x73\x69\x7A\x65","\x4E\x63\x65\x50\x75","\x61\x67\x6F\x64\x65\x73\x61\x69\x6E\x2E","\x75\x79\x4F\x43\x67","\x69\x6E\x3A\x61\x75\x74\x6F\x3B\x20\x6D","\x37\x7C\x33\x7C\x36","\x6C\x69\x67\x68\x74","\x6D\x73\x61\x70\x70\x6C\x69\x63\x61\x74","\x6E\x50\x55\x6C\x78","\x20\x20\x20\x20\x3C\x2F\x61\x3E\x0A\x20","\x66\x6C\x65\x78\x20\x62\x61\x73\x65\x6C","\x22\x20\x64\x61\x74\x61\x2D\x74\x65\x78","\x36\x39\x39\x22\x3E\x3C\x2F\x70\x61\x74","\x49\x75\x46\x41\x6C","\x64\x76\x49\x63\x64","\x20\x55\x49\x3C\x2F\x73\x70\x61\x6E\x3E","\x72\x2D\x73\x74\x79\x6C\x65\x5D","\x64\x69\x76\x3E\x0A","\x32\x7C\x34\x7C\x33\x7C\x31\x7C\x30","\x70\x58\x69\x78\x6D","\x42\x79\x49\x64","\x36\x37\x33\x33\x38\x38\x30\x75\x4D\x4B\x65\x70\x6F","\x69\x6E\x64\x65\x78\x4F\x66","\x75\x73\x3C\x2F\x73\x70\x61\x6E\x3E\x0A","\x2D\x2D\x76\x48\x65\x69\x67\x68\x74","\x73\x74\x79\x6C\x65","\x74\x73\x2F\x73\x75\x6D\x6D\x61\x72\x79","\x71\x69\x54\x64\x76","\x34\x20\x32\x34\x22\x3E\x3C\x70\x61\x74","\x6C\x79\x2E","\x4E\x74\x43\x67\x4D","\x41\x75\x52\x49\x54","\x20\x6D\x61\x72\x67\x69\x6E\x2D\x62\x6C","\x53\x4B\x65\x4A\x73","\x33\x7C\x31\x30\x7C\x34\x7C\x31\x31\x7C","\x73\x65\x3B\x20\x66\x6F\x6E\x74\x2D\x77","\x4D\x5A\x4A\x6C\x72","\x63\x6C\x61\x73\x73\x4C\x69\x73\x74","\x75\x6E\x64\x65\x66\x69\x6E\x65\x64","\x61\x64\x64","\x74\x68\x3E\x3C\x2F\x73\x76\x67\x3E\x0A","\x78\x20\x63\x49\x6E\x68\x65\x72\x69\x74","\x61\x6D\x51\x72\x48","\x69\x72\x44\x48\x55","\x68\x54\x72\x6C\x68","\x74\x6F\x72\x41\x6C\x6C","\x64\x61\x72\x6B","\x3B\x6C\x69\x6E\x65\x2D\x68\x65\x69\x67","\x6F\x70\x65\x6E\x53\x65\x61\x72\x63\x68","\x73\x63\x72\x6F\x6C\x6C\x54\x6F\x70","\x68\x65\x6D\x65\x20\x6C\x65\x67\x61\x6C","\x74\x65\x78\x74\x29\x3B\x20\x66\x6C\x65","\x74\x69\x6D\x65\x6F\x75\x74","\x68\x65\x61\x64","\x32\x30\x70\x78\x7D\x20\x2E\x69\x6E\x4C","\x6A\x67\x76\x58\x45","\x69\x78\x44\x4A\x41","\x2F\x66\x65\x65\x64\x73\x2F\x70\x6F\x73","\x22\x4D\x33\x2E\x35\x20\x31\x32\x48\x32","\x23\x31\x65\x31\x65\x31\x65","\x76\x20\x63\x6C\x61\x73\x73\x3D\x22\x69","\x64\x69\x76","\x61\x74\x74\x72\x28\x64\x61\x74\x61\x2D","\x6D\x52\x48\x71\x46","\x4A\x62\x72\x73\x61","\x38\x53\x46\x52\x4D\x59\x5A","\x20\x75\x22\x3E\x0A\x20\x20\x3C\x64\x69","\x7A\x64\x71\x6E\x64","\x73\x65\x74\x50\x72\x6F\x70\x65\x72\x74","\x27\x6E\x6F\x74\x65\x20\x77\x72\x27\x3E","\x6E\x3E\x43\x6F\x6E\x74\x61\x63\x74\x20","\x69\x69\x41\x68\x43","\x20\x3C\x70\x20\x63\x6C\x61\x73\x73\x3D","\x63\x6C\x61\x73\x73","\x20\x20\x3C\x2F\x64\x69\x76\x3E\x0A\x20","\x63\x74\x2E\x68\x74\x6D\x6C\x22\x3E\x0A","\x70\x65\x72\x20\x74\x6F\x20\x61\x63\x74","\x0A\x2E\x69\x6E\x4C\x7B\x77\x69\x64\x74","\x73\x3D\x22\x69\x6E\x4C\x20\x66\x6C\x65","\x29\x3B\x70\x61\x64\x64\x69\x6E\x67\x3A","\x69\x6E\x67\x20\x74\x68\x69\x73\x20\x74","\x62\x6F\x64\x79","\x46\x78\x53\x47\x74","\x6E\x4C\x63\x20\x66\x6C\x65\x78\x20\x63","\x73\x3A\x2F\x2F\x77\x77\x77\x2E\x6A\x61","\x66\x61\x6C\x73\x65","\x54\x49\x4C\x4E\x51","\x35\x7C\x31\x7C\x32\x7C\x30\x7C\x34\x7C","\x63\x69\x75\x67\x58","\x74\x20\x72\x65\x67\x69\x73\x74\x65\x72","\x72\x6D\x3A\x75\x70\x70\x65\x72\x63\x61","\x6A\x64\x55\x42\x44","\x6C\x74\x73","\x6E\x65\x20\x72\x22\x20\x76\x69\x65\x77","\x63\x7B\x67\x61\x70\x3A\x35\x70\x78\x3B","\x30\x7C\x34\x7C\x31\x7C\x35\x7C\x32\x7C","\x4D\x65\x64\x69\x61\x6E\x20\x55\x49","\x4E\x65\x41\x61\x69","\x68\x42\x4D\x69\x61","\x67\x4E\x6D\x47\x71","\x54\x68\x65\x20\x64\x6F\x6D\x61\x69\x6E","\x45\x76\x79\x59\x79","\x68\x74\x74\x70\x73\x3A\x2F\x2F\x77\x77","\x73\x63\x72\x69\x70\x74","\x20\x69\x31\x38\x22\x20\x61\x72\x69\x61","\x6D\x65\x74\x61\x5B\x6E\x61\x6D\x65\x3D","\x65\x21\x20\x54\x68\x61\x6E\x6B\x20\x79","\x68\x74\x3A\x31\x2E\x34\x7D\x20\x2E\x69","\x65\x6D\x62\x65\x64","\x30\x2E\x33\x33\x22\x3E\x3C\x2F\x70\x61","\x3C\x2F\x75\x3E\x20\x69\x73\x20\x6E\x6F","\x3E\x3A\x20\x3C\x61\x20\x63\x6C\x61\x73","\x35\x30\x67\x55\x4D\x61\x4E\x66","\x66\x72\x61\x6D\x65\x62\x6F\x72\x64\x65","\x6F\x6C\x75\x6D\x6E\x22\x3E\x0A\x20\x20","\x75\x5A\x66\x6A\x6C","\x67\x73\x59\x4B\x63","\x37\x77\x47\x47\x53\x5A\x66","\x74\x6F\x72","\x63\x6C\x69\x63\x6B","\x72\x65\x6D\x6F\x76\x65","\x6B\x4A\x5A\x65\x74","\x6C\x6F\x61\x64\x65\x64","\x20\x64\x6F\x6D\x61\x69\x6E\x2E\x3C\x2F","\x42\x70\x7A\x77\x52","\x69\x6E\x65\x22\x20\x64\x61\x74\x61\x2D","\x6C\x65\x2D\x77\x65\x62\x2D\x61\x70\x70","\x63\x6F\x6D\x2F\x76\x69\x2F","\x73\x42\x79\x43\x6C\x61\x73\x73\x4E\x61","\x20\x3C\x2F\x64\x69\x76\x3E\x0A\x3C\x2F","\x73\x3D\x22\x69\x6E\x4C\x62\x20\x62\x75","\x7C\x37\x7C\x32\x7C\x36\x7C\x31\x33\x7C","\x2D\x72\x65\x73\x75\x6C\x74\x73\x3D\x39","\x74\x3D\x22\x50\x72\x6F\x64\x75\x63\x74","\x64\x65\x66\x61\x75\x6C\x74","\x74\x20\x69\x6E\x70\x75\x74\x5B\x74\x79","\x68\x69\x73\x20\x74\x68\x65\x6D\x65\x20","\x73\x3D\x22\x65\x78\x74\x4C\x22\x20\x68","\x46\x65\x65\x64\x20\x6E\x6F\x74\x20\x66","\x74\x72\x75\x65","\x3C\x2F\x73\x70\x61\x6E\x3E\x0A\x20\x20","\x67\x2E\x79\x6F\x75\x74\x75\x62\x65\x2E","\x69\x6F\x6E\x2D\x6E\x61\x76\x62\x75\x74","\x6F\x75\x6E\x64","\x65\x64\x2E\x20\x42\x75\x79\x20\x74\x68","\x6C\x69\x63\x65\x6E\x73\x65\x2E\x6A\x61","\x62\x61\x63\x6B\x67\x72\x6F\x75\x6E\x64","\x78\x3A\x30\x20\x30\x20\x38\x30\x70\x78","\x68\x3A\x31\x30\x30\x25\x3B\x68\x65\x69","\x61\x6C\x6C\x6F\x77\x66\x75\x6C\x6C\x73","\x28\x2D\x2D\x76\x48\x65\x69\x67\x68\x74","\x63\x6F\x6E\x74\x65\x6E\x74","\x61\x70\x70\x65\x6E\x64\x43\x68\x69\x6C","\x31\x34\x30\x32\x30\x39\x38\x7A\x48\x46\x65\x45\x5A","\x68\x3E\x3C\x70\x61\x74\x68\x20\x64\x3D","\x35\x31\x37\x30\x30\x43\x66\x6E\x78\x6A\x63","\x6E\x20\x69\x73\x20\x69\x6E\x61\x63\x74","\x2E\x6C\x61\x7A\x79","\x65\x69\x67\x68\x74\x3A\x35\x30\x30\x7D","\x6E\x44\x61\x74\x61","\x4B\x66\x72\x6A\x61","\x69\x64\x67\x65\x74\x20\x69\x6E\x70\x75","\x65\x7B\x63\x6F\x6E\x74\x65\x6E\x74\x3A","\x6B\x53\x77\x47\x52","\x74\x5D\x2C\x20\x2E\x77\x69\x64\x67\x65","\x66\x58\x44\x59\x71","\x74\x69\x74\x6C\x65","\x61\x78\x2D\x77\x69\x64\x74\x68\x3A\x34","\x70\x64\x61\x74\x65\x64\x26\x6D\x61\x78","\x48\x61\x70\x6C\x6D","\x63\x68\x65\x63\x6B\x44\x6F\x6D\x61\x69","\x50\x68\x4F\x43\x65","\x2D\x69\x6E\x2D\x73\x63\x72\x69\x70\x74","\x2F\x3F\x61\x6C\x74\x3D\x6A\x73\x6F\x6E","\x20\x3C\x75\x3E","\x61\x59\x69\x47\x43","\x20\x20\x20\x20\x3C\x73\x70\x61\x6E\x20","\x74\x65\x78\x74\x3D\x22\x57\x65\x62\x22","\x74\x6F\x70\x6C\x61\x79\x3D\x31","\x47\x59\x68\x4A\x4A","\x42\x6F\x78\x3D\x22\x30\x20\x30\x20\x32","\x63\x72\x65\x65\x6E","\x73\x4C\x50\x59\x5A","\x31\x33\x37\x37\x37\x31\x38\x31\x4D\x64\x59\x78\x50\x73","\x46\x47\x53\x73\x59","\x63\x6F\x6D\x22\x3E\x4A\x61\x67\x6F\x20","\x6C\x69\x6E\x6B","\x6F\x6E\x73\x63\x72\x6F\x6C\x6C","\x65\x6D\x65\x6E\x74","\x67\x65\x74\x45\x6C\x65\x6D\x65\x6E\x74","\x64\x6F\x63\x75\x6D\x65\x6E\x74\x45\x6C","\x69\x6E\x2D\x73\x63\x72\x69\x70\x74\x26","\x61\x70\x70\x6C\x65\x2D\x6D\x6F\x62\x69","\x54\x4E\x64\x44\x50","\x34\x36\x33\x31\x30\x37\x79\x71\x54\x63\x51\x46","\x54\x61\x43\x42\x42","\x2E\x69\x6E\x4C\x63\x20\x3E\x2A\x7B\x63","\x76\x6F\x72\x57\x5A","\x73\x65\x74\x49\x74\x65\x6D","\x63\x6F\x6D\x2F\x65\x6D\x62\x65\x64\x2F","\x2D\x73\x74\x61\x74\x75\x73\x2D\x62\x61","\x6F\x6C\x75\x6D\x6E\x2D\x67\x61\x70\x3A","\x68\x65\x69\x67\x68\x74\x3A\x76\x61\x72","\x2D\x73\x69\x7A\x65\x3A\x31\x34\x70\x78","\x35\x72\x63\x64\x57\x4A\x5A","\x20\x20\x20\x20\x20\x20\x3C\x73\x76\x67","\x0A\x3C\x64\x69\x76\x20\x63\x6C\x61\x73","\x69\x76\x61\x74\x65\x20\x74\x68\x69\x73","\x61\x6E\x20\x63\x6C\x61\x73\x73\x3D\x22","\x26\x6F\x72\x64\x65\x72\x62\x79\x3D\x75","\x74\x68\x65\x6D\x65","\x52\x74\x7A\x70\x4F","\x64\x65\x6F","\x78\x20\x62\x61\x73\x65\x6C\x69\x6E\x65","\x6E\x54\x69\x74\x6C\x65","\x2D\x63\x6F\x6C\x6F\x72\x3A\x23\x66\x66","\x68\x72\x65\x66\x3D\x22\x68\x74\x74\x70","\x6F\x6D\x2F\x70\x2F\x63\x6F\x6E\x74\x61","\x64\x77\x63\x73\x42","\x3F\x61\x6C\x74\x3D\x6A\x73\x6F\x6E\x2D","\x65\x78\x74\x61\x72\x65\x61","\x6E\x20\x69\x73\x20\x61\x63\x74\x69\x76","\x34\x34\x36\x33\x37\x33\x44\x6F\x49\x5A\x57\x53","\x64\x6F\x6D","\x54\x72\x62\x54\x73","\x33\x31\x35\x35\x39\x34\x69\x52\x63\x50\x50\x4D","\x64\x41\x6A\x4E\x4B","\x3A\x2F\x2F\x74\x68\x65\x6D\x65\x2E\x6A","\x6C\x61\x7A\x79","\x39\x39\x39\x26\x63\x61\x6C\x6C\x62\x61","\x6C\x6F\x67","\x67\x6F\x64\x65\x73\x61\x69\x6E\x2E\x63","\x74\x74\x6F\x6E\x20\x73\x63\x20\x6F\x70","\x74\x5B\x74\x79\x70\x65\x3D\x74\x65\x78","\x67\x65\x74\x41\x74\x74\x72\x69\x62\x75","\x72\x65\x66\x3D\x22\x68\x74\x74\x70\x73","\x74\x6F\x6E\x2D\x63\x6F\x6C\x6F\x72\x5D","\x59\x6F\x75\x74\x75\x62\x65\x20\x76\x69","\x20\x3E\x2A\x3A\x3A\x62\x65\x66\x6F\x72","\x20\x73\x75\x70\x70\x6F\x72\x74\x20\x75","\x2F\x73\x64\x64\x65\x66\x61\x75\x6C\x74","\x68\x72\x65\x66","\x74\x45\x63\x4E\x5A","\x4D\x6B\x6F\x57\x63","\x0A\x20\x20\x20\x20\x20\x20\x3C\x73\x70","\x67\x65\x74\x49\x74\x65\x6D","\x72\x65\x6C","\x5A\x6F\x61\x67\x49","\x44\x65\x73\x61\x69\x6E\x3C\x2F\x61\x3E","\x75\x44\x4C\x6E\x7A","\x68\x6F\x73\x74\x6E\x61\x6D\x65","\x6E\x51\x4D\x56\x72","\x69\x73\x20\x70\x72\x6F\x64\x75\x63\x74","\x2E\x6A\x70\x67","\x70\x3E\x0A\x20\x20\x20\x20\x3C\x64\x69","\x67\x68\x74\x3A\x31\x30\x30\x76\x68\x3B","\x74\x68\x65\x6D\x65\x2D\x63\x6F\x6C\x6F","\x72\x5D","\x64\x61\x74\x61\x2D\x74\x68\x65\x6D\x65"];var license_0x47ae09=license_0x5084;(function(_0x232cx2,_0x232cx3){var _0x232cx4=license_0x5084;var _0x232cx5=_0x232cx2();while(!![]){try{var _0x232cx6=parseInt(_0x232cx4(0x18b))/ 0x1+ parseInt(_0x232cx4(0x189))/ 0x2+ parseInt(_0x232cx4(0x1b8))/ 0x3* (parseInt(_0x232cx4(0x12a))/ 0x4)+ parseInt(_0x232cx4(0xaa))/ 0x5* (parseInt(_0x232cx4(0xc0))/ 0x6)+ -parseInt(_0x232cx4(0x161))/ 0x7 * (-parseInt(_0x232cx4(0xf9))/ 0x8)+ -parseInt(_0x232cx4(0xbd))/ 0x9 * (parseInt(_0x232cx4(0x15b))/ 0xa)+ -parseInt(_0x232cx4(0x1ad))/ 0xb;if(_0x232cx6=== _0x232cx3){break}else {_0x232cx5[_0x91f0[1]](_0x232cx5[_0x91f0[0]]())}}catch(_0x35ecb1){_0x232cx5[_0x91f0[1]](_0x232cx5[_0x91f0[0]]())}}}(license_0x79eb,0x6f2c5));dataProduct= license_0x47ae09(0x14b);databaseDomain= license_0x47ae09(0x181)+ license_0x47ae09(0xc7)+ _0x91f0[2];triggerError= _0x91f0[3];triggerType= license_0x47ae09(0x11b);const cssFixed=license_0x47ae09(0x137)+ license_0x47ae09(0x184)+ license_0x47ae09(0xe2)+ license_0x47ae09(0xa8)+ license_0x47ae09(0x186)+ license_0x47ae09(0x13a)+ _0x91f0[4]+ _0x91f0[5]+ license_0x47ae09(0x182)+ license_0x47ae09(0xb5)+ _0x91f0[6]+ license_0x47ae09(0xa9)+ license_0x47ae09(0x116)+ license_0x47ae09(0x156)+ _0x91f0[7]+ license_0x47ae09(0xe7)+ license_0x47ae09(0x199)+ license_0x47ae09(0x11d)+ license_0x47ae09(0x149)+ license_0x47ae09(0x105)+ _0x91f0[8]+ license_0x47ae09(0x1ba)+ license_0x47ae09(0xa7)+ _0x91f0[9]+ license_0x47ae09(0xcf)+ license_0x47ae09(0x194)+ license_0x47ae09(0x125)+ license_0x47ae09(0x11a)+ license_0x47ae09(0x183)+ _0x91f0[10]+ _0x91f0[11]+ license_0x47ae09(0x145)+ license_0x47ae09(0x108)+ license_0x47ae09(0x190)+ _0x91f0[12];const htmlFixed=license_0x47ae09(0xac)+ license_0x47ae09(0x138)+ license_0x47ae09(0x10e)+ license_0x47ae09(0x12b)+ license_0x47ae09(0x123)+ _0x91f0[13]+ license_0x47ae09(0x131)+ license_0x47ae09(0x12e)+ license_0x47ae09(0x14f)+ license_0x47ae09(0x1a0)+ window[_0x91f0[14]][license_0x47ae09(0xdc)]+ (license_0x47ae09(0x159)+ license_0x47ae09(0x144)+ license_0x47ae09(0x180)+ license_0x47ae09(0xde)+ _0x91f0[15]+ _0x91f0[16]+ _0x91f0[17]+ license_0x47ae09(0x136)+ license_0x47ae09(0xad)+ license_0x47ae09(0x16a)+ license_0x47ae09(0xe0)+ license_0x47ae09(0x123)+ license_0x47ae09(0x13e)+ license_0x47ae09(0x15d)+ license_0x47ae09(0x1a4)+ _0x91f0[18]+ license_0x47ae09(0xb3)+ license_0x47ae09(0xee)+ license_0x47ae09(0x175)+ _0x91f0[19]+ license_0x47ae09(0xf2)+ license_0x47ae09(0xd5)+ license_0x47ae09(0xae)+ license_0x47ae09(0xed)+ license_0x47ae09(0x16c)+ license_0x47ae09(0x1a5)+ license_0x47ae09(0x15a)+ license_0x47ae09(0x179)+ license_0x47ae09(0xcc)+ license_0x47ae09(0xc2)+ license_0x47ae09(0xe5)+ license_0x47ae09(0x1af)+ license_0x47ae09(0xda)+ license_0x47ae09(0x17c)+ license_0x47ae09(0x133)+ _0x91f0[20]+ license_0x47ae09(0x171)+ license_0x47ae09(0xc8)+ license_0x47ae09(0x153)+ _0x91f0[21]+ _0x91f0[22]+ license_0x47ae09(0xb6)+ license_0x47ae09(0x13f)+ license_0x47ae09(0xc7)+ license_0x47ae09(0xb7)+ license_0x47ae09(0x134)+ _0x91f0[23]+ license_0x47ae09(0x12f)+ license_0x47ae09(0xfb)+ license_0x47ae09(0xab)+ _0x91f0[24]+ license_0x47ae09(0x148)+ license_0x47ae09(0x1a8)+ license_0x47ae09(0x101)+ _0x91f0[25]+ _0x91f0[26]+ _0x91f0[27]+ _0x91f0[28]+ _0x91f0[29]+ license_0x47ae09(0xef)+ license_0x47ae09(0x18a)+ license_0x47ae09(0x121)+ license_0x47ae09(0x158)+ license_0x47ae09(0x10d)+ license_0x47ae09(0xec)+ license_0x47ae09(0x170)+ license_0x47ae09(0xf4));function showPopUpEror(){var _0x232cxa=license_0x47ae09;var _0x232cxb={'\x41\x75\x52\x49\x54':_0x232cxa(0x124),'\x4A\x62\x72\x73\x61':_0x232cxa(0xfe),'\x42\x70\x7A\x77\x52':function(_0x232cxc,_0x232cxd){return _0x232cxc== _0x232cxd},'\x6A\x64\x55\x42\x44':_0x232cxa(0x11b),'\x74\x45\x63\x4E\x5A':function(_0x232cxe,_0x232cxf,_0x232cx10){return _0x232cxe(_0x232cxf,_0x232cx10)},'\x68\x54\x72\x6C\x68':_0x91f0[30],'\x6E\x50\x55\x6C\x78':function(_0x232cx11,_0x232cx12,_0x232cx13){return _0x232cx11(_0x232cx12,_0x232cx13)}};var _0x232cx14=document[_0x232cxa(0xd9)+ _0x91f0[31]](_0x232cxb[_0x232cxa(0x104)]);var _0x232cx15=document[_0x91f0[32]+ _0x232cxa(0x172)](_0x232cxb[_0x232cxa(0x127)]);_0x232cx15[_0x232cxa(0x128)]= cssFixed;_0x232cx14[_0x91f0[33]]= htmlFixed;document[_0x232cxa(0x11c)][_0x232cxa(0x163)](_0x232cx15);if(_0x232cxb[_0x232cxa(0x16b)](triggerType,_0x232cxb[_0x232cxa(0x146)])){_0x232cxb[_0x232cxa(0xd3)](setTimeout,function(){var _0x232cx16=_0x232cxa;document[_0x232cx16(0x13c)][_0x232cx16(0x128)]= _0x91f0[34];document[_0x232cx16(0x13c)][_0x91f0[35]](_0x232cx14)},0x1f4)};if(_0x232cxb[_0x232cxa(0x16b)](triggerType,_0x232cxb[_0x232cxa(0x111)])){_0x232cxb[_0x232cxa(0xeb)](setInterval,function(){var _0x232cx17=_0x232cxa;document[_0x232cx17(0x13c)][_0x232cx17(0x128)]= _0x91f0[34];document[_0x232cx17(0x13c)][_0x232cx17(0x163)](_0x232cx14)},0x1f4)}}if(document[license_0x47ae09(0x1b3)+ license_0x47ae09(0xf8)](triggerError)){var StatusActiveDomain=function(_0x232cx19){var _0x232cx1a=license_0x47ae09;var _0x232cx1b={'\x64\x77\x63\x73\x42':function(_0x232cx1c,_0x232cx1d){return _0x232cx1c== _0x232cx1d},'\x67\x73\x59\x4B\x63':function(_0x232cx1e){return _0x232cx1e()},'\x51\x52\x76\x61\x79':_0x232cx1a(0x168)+ _0x232cx1a(0x18d)+ _0x91f0[36]+ _0x232cx1a(0x178)+ _0x91f0[37]+ _0x232cx1a(0xd0)+ _0x91f0[38]};console[_0x232cx1a(0xc5)](_0x91f0[39]+ _0x232cx1a(0xbc)+ _0x232cx1a(0x155)+ _0x91f0[40]+ _0x232cx1a(0x13b)+ _0x232cx1a(0x119)+ _0x232cx1a(0x102)+ _0x91f0[41])}}else {showPopUpEror()};function getFeeds(_0x232cx20,_0x232cx21){var _0x232cx22=license_0x47ae09;var _0x232cx23={};_0x232cx23[_0x232cx22(0x1bb)]= _0x232cx22(0xf5);_0x232cx23[_0x232cx22(0x109)]= _0x232cx22(0x152);var _0x232cx24=_0x232cx23;var _0x232cx25=_0x232cx24[_0x232cx22(0x1bb)][_0x232cx22(0x160)](_0x91f0[42]);var _0x232cx26=0x0;while(!![]){switch(_0x232cx25[_0x232cx26++]){case _0x91f0[44]:document[_0x232cx22(0x1b3)+ _0x232cx22(0xf8)](_0x91f0[43])[_0x232cx22(0x166)]();continue;case _0x91f0[45]:document[_0x232cx22(0x11c)][_0x232cx22(0x163)](_0x232cx27);continue;case _0x91f0[46]:var _0x232cx27=document[_0x232cx22(0xd9)+ _0x91f0[31]](_0x232cx24[_0x232cx22(0x109)]);continue;case _0x91f0[48]:_0x232cx27[_0x91f0[47]]= _0x91f0[43];continue;case _0x91f0[50]:_0x232cx27[_0x91f0[49]]= _0x232cx20+ _0x232cx21;continue};break}}getFeeds(_0x91f0[51]+ databaseDomain+ (license_0x47ae09(0x120)+ license_0x47ae09(0xff)+ license_0x47ae09(0x19f)+ license_0x47ae09(0x19e)+ license_0x47ae09(0xaf)+ license_0x47ae09(0x19a)+ license_0x47ae09(0x174)+ license_0x47ae09(0xc4)+ _0x91f0[52]),license_0x47ae09(0x19c)+ license_0x47ae09(0x191));function license_0x5084(_0x232cx29,_0x232cx2a){var _0x232cx2b=license_0x79eb();license_0x5084= function(_0x232cx2c,_0x232cx2d){_0x232cx2c= _0x232cx2c- 0xa6;var _0x232cx2e=_0x232cx2b[_0x232cx2c];return _0x232cx2e};return license_0x5084(_0x232cx29,_0x232cx2a)}function checkDomainData(_0x232cx19){var _0x232cx30=license_0x47ae09;var _0x232cx31={'\x58\x55\x56\x4C\x59':_0x91f0[53]+ _0x232cx30(0x173)+ _0x232cx30(0x107)+ _0x91f0[54],'\x52\x74\x7A\x70\x4F':function(_0x232cx32,_0x232cx33){return _0x232cx32> _0x232cx33},'\x64\x41\x6A\x4E\x4B':function(_0x232cx34,_0x232cx35){return _0x232cx34<= _0x232cx35},'\x62\x42\x77\x62\x45':function(_0x232cx36,_0x232cx37){return _0x232cx36< _0x232cx37},'\x46\x78\x53\x47\x74':function(_0x232cx38,_0x232cx39){return _0x232cx38=== _0x232cx39},'\x75\x66\x6E\x63\x4E':function(_0x232cx3a,_0x232cx3b){return _0x232cx3a=== _0x232cx3b},'\x6D\x52\x48\x71\x46':_0x232cx30(0x17a)+ _0x232cx30(0x17f),'\x75\x79\x4F\x43\x67':function(_0x232cx3c,_0x232cx3d,_0x232cx3e){return _0x232cx3c(_0x232cx3d,_0x232cx3e)},'\x5A\x6F\x61\x67\x49':function(_0x232cx3f,_0x232cx40){return _0x232cx3f+ _0x232cx40},'\x48\x61\x70\x6C\x6D':_0x232cx30(0xba)+ _0x232cx30(0x1b5)+ _0x91f0[55],'\x4E\x63\x65\x50\x75':function(_0x232cx41,_0x232cx42){return _0x232cx41< _0x232cx42}};var _0x232cx43=_0x232cx31[_0x91f0[57]][_0x91f0[56]](_0x91f0[42]);var _0x232cx44=0x0;while(!![]){switch(_0x232cx43[_0x232cx44++]){case _0x91f0[44]:if(_0x232cx31[_0x232cx30(0xb1)](_0x232cx46,0x96)){var _0x232cx45=0x96};continue;case _0x91f0[45]:var _0x232cx46=_0x232cx4a[_0x232cx30(0x117)+ _0x91f0[59]+ _0x232cx30(0x147)][_0x91f0[58]];continue;case _0x91f0[46]:var _0x232cx47= new Array();continue;case _0x91f0[48]:;;;;continue;case _0x91f0[50]:;;;;continue;case _0x91f0[54]:;;;;continue;case _0x91f0[60]:var _0x232cx48= new Array();continue;case _0x91f0[61]:;;;;continue;case _0x91f0[62]:if(_0x232cx31[_0x232cx30(0xc1)](_0x232cx46,0x96)){var _0x232cx45=_0x232cx46};continue;case _0x91f0[63]:;;;;continue;case _0x91f0[65]:for(var _0x232cx49=0x0;_0x232cx31[_0x91f0[64]](_0x232cx49,_0x232cx45);_0x232cx49++){if(_0x232cx31[_0x232cx30(0x13d)](_0x232cx4a[_0x232cx30(0xe1)][_0x232cx49][_0x232cx30(0x198)].$t,undefined)){}else {_0x232cx48[_0x232cx49]= _0x232cx4a[_0x232cx30(0xe1)][_0x232cx49][_0x232cx30(0x198)][_0x91f0[58]]}};continue;case _0x91f0[66]:if(_0x232cx31[_0x232cx30(0xf7)](_0x232cx47[_0x232cx48[_0x232cx30(0xfa)](dataProduct)],undefined)){console[_0x232cx30(0xc5)](_0x232cx31[_0x232cx30(0x126)])}else {_0x232cx31[_0x232cx30(0xe6)](getFeeds,_0x232cx31[_0x232cx30(0xd8)](_0x232cx47[_0x232cx48[_0x232cx30(0xfa)](dataProduct)],_0x232cx31[_0x232cx30(0x19b)]),_0x232cx30(0x19c)+ _0x232cx30(0xb4))};continue;case _0x91f0[68]:var _0x232cx4a=_0x232cx19[_0x91f0[67]];continue;case _0x91f0[71]:for(var _0x232cx4b=0x0;_0x232cx31[_0x232cx30(0xe4)](_0x232cx4b,_0x232cx45);_0x232cx4b++){if(_0x232cx4a[_0x232cx30(0xe1)][_0x232cx4b][_0x232cx30(0x1b0)][0x3]=== undefined){if(_0x232cx31[_0x91f0[70]](_0x232cx4a[_0x91f0[69]][_0x232cx4b][_0x232cx30(0x1b0)][0x1][_0x232cx30(0xd7)],undefined)){}else {_0x232cx47[_0x232cx4b]= _0x232cx4a[_0x232cx30(0xe1)][_0x232cx4b][_0x232cx30(0x1b0)][0x1][_0x232cx30(0xd2)]}}else {_0x232cx47[_0x232cx4b]= _0x232cx4a[_0x232cx30(0xe1)][_0x232cx4b][_0x232cx30(0x1b0)][0x3][_0x232cx30(0xd2)]}};continue};break}}function checkDomainTitle(_0x232cx4d){var _0x232cx4e=license_0x47ae09;var _0x232cx4f={'\x54\x72\x62\x54\x73':function(_0x232cx50,_0x232cx51){return _0x232cx50=== _0x232cx51},'\x49\x75\x46\x41\x6C':function(_0x232cx52,_0x232cx53){return _0x232cx52< _0x232cx53},'\x66\x58\x44\x59\x71':function(_0x232cx54,_0x232cx55){return _0x232cx54(_0x232cx55)},'\x71\x69\x54\x64\x76':function(_0x232cx56,_0x232cx57){return _0x232cx56(_0x232cx57)}};if(_0x232cx4f[_0x232cx4e(0xbf)](_0x232cx4d[_0x232cx4e(0xe1)][_0x232cx4e(0x187)],undefined)){}else {var _0x232cx58=_0x232cx4d[_0x91f0[69]][_0x232cx4e(0x187)][_0x91f0[58]];_0x232cx4f[_0x232cx4e(0x197)](StatusActiveDomain,![])}}document[license_0x47ae09(0x1b3)+ license_0x47ae09(0x16f)+ _0x91f0[73]](_0x91f0[3])[0x0][license_0x47ae09(0x10a)][license_0x47ae09(0x166)](_0x91f0[72]);var inputs=document[license_0x47ae09(0xcb)+ license_0x47ae09(0x112)](_0x91f0[74]+ _0x91f0[75]+ _0x91f0[76]+ license_0x47ae09(0x193)+ license_0x47ae09(0xc9)+ license_0x47ae09(0x196)+ license_0x47ae09(0x177)+ _0x91f0[77]+ _0x91f0[78]+ license_0x47ae09(0xbb));for(var i=0x0;i< inputs[_0x91f0[79]];i++){var input=inputs[i];input[license_0x47ae09(0xc6)+ license_0x47ae09(0xb9)](_0x91f0[80],function(){var _0x232cx5c=license_0x47ae09;var _0x232cx5d={};_0x232cx5d[_0x91f0[81]]= _0x232cx5c(0x17b);_0x232cx5d[_0x232cx5c(0x143)]= _0x232cx5c(0x140);var _0x232cx5e=_0x232cx5d;var _0x232cx5f=this[_0x91f0[82]]?_0x232cx5e[_0x232cx5c(0x1ac)]:_0x232cx5e[_0x232cx5c(0x143)];this[_0x232cx5c(0x1a3)+ _0x91f0[84]](_0x91f0[83],_0x232cx5f)})};window[license_0x47ae09(0x1b1)]= function(){var _0x232cx60=license_0x47ae09;var _0x232cx61={};_0x232cx61[_0x91f0[85]]= _0x91f0[86];_0x232cx61[_0x232cx60(0x103)]= function(_0x232cx62,_0x232cx63){return _0x232cx62> _0x232cx63};_0x232cx61[_0x232cx60(0x1a7)]= function(_0x232cx64,_0x232cx65){return _0x232cx64> _0x232cx65};var _0x232cx66=_0x232cx61;const _0x232cx67=document[_0x232cx60(0xcb)+ _0x232cx60(0x162)](_0x232cx66[_0x232cx60(0x129)])[_0x232cx60(0x10a)];if(_0x232cx66.NtCgM(document[_0x232cx60(0x13c)][_0x232cx60(0x118)],0x14)|| _0x232cx66.GYhJJ(document[_0x232cx60(0x1b4)+ _0x232cx60(0x1b2)][_0x232cx60(0x118)],0x14)){_0x232cx67[_0x232cx60(0x10c)](_0x91f0[87])}else {_0x232cx67[_0x232cx60(0x166)](_0x91f0[87])}};(function(){var _0x232cx68=license_0x47ae09;var _0x232cx69={};_0x232cx69[_0x232cx68(0x141)]= _0x232cx68(0x14a)+ _0x91f0[48];_0x232cx69[_0x91f0[88]]= _0x91f0[89];_0x232cx69[_0x91f0[90]]= _0x232cx68(0x185)+ _0x232cx68(0x1aa);_0x232cx69[_0x232cx68(0xf1)]= _0x232cx68(0x15c)+ _0x91f0[91];_0x232cx69[_0x232cx68(0x195)]= _0x232cx68(0x165);_0x232cx69[_0x232cx68(0x1a1)]= function(_0x232cx6a,_0x232cx6b){return _0x232cx6a+ _0x232cx6b};_0x232cx69[_0x232cx68(0x14d)]= function(_0x232cx6c,_0x232cx6d){return _0x232cx6c+ _0x232cx6d};_0x232cx69[_0x232cx68(0x15e)]= _0x232cx68(0x151)+ _0x91f0[92]+ _0x232cx68(0x1bd);_0x232cx69[_0x232cx68(0x14e)]= _0x91f0[93];_0x232cx69[_0x91f0[94]]= function(_0x232cx6e,_0x232cx6f){return _0x232cx6e< _0x232cx6f};_0x232cx69[_0x232cx68(0xf6)]= _0x232cx68(0x142)+ _0x232cx68(0xe8);_0x232cx69[_0x232cx68(0x115)]= _0x232cx68(0x132);_0x232cx69[_0x232cx68(0x12c)]= _0x232cx68(0xd1)+ _0x232cx68(0xdf);_0x232cx69[_0x232cx68(0x11e)]= _0x232cx68(0x164);_0x232cx69[_0x232cx68(0x1ab)]= _0x91f0[95];_0x232cx69[_0x232cx68(0x150)]= _0x232cx68(0xce)+ _0x232cx68(0xb2);var _0x232cx70=_0x232cx69;var _0x232cx71=document[_0x232cx68(0xcb)+ _0x232cx68(0x112)](_0x232cx70[_0x232cx68(0x14e)]);for(var _0x232cx72=0x0;_0x232cx70.JkmRS(_0x232cx72,_0x232cx71[_0x232cx68(0x139)]);_0x232cx72++){var _0x232cx73=_0x232cx70[_0x232cx68(0xf6)][_0x232cx68(0x160)](_0x91f0[42]);var _0x232cx74=0x0;while(!![]){switch(_0x232cx73[_0x232cx74++]){case _0x91f0[44]:_0x232cx75[_0x91f0[97]+ _0x91f0[84]](_0x91f0[96],_0x232cx77);continue;case _0x91f0[45]:var _0x232cx75= new Image();continue;case _0x91f0[46]:_0x232cx75[_0x91f0[97]+ _0x91f0[84]](_0x232cx70[_0x91f0[98]],_0x232cx68(0xc3));continue;case _0x91f0[48]:_0x232cx75[_0x232cx68(0xc6)+ _0x232cx68(0xb9)](_0x232cx68(0x18f),(function(){var _0x232cx76=_0x232cx68;_0x232cx71[_0x232cx72][_0x232cx76(0x188)+ _0x91f0[99]](_0x232cx75)}(_0x232cx72)));continue;case _0x91f0[50]:_0x232cx75[_0x232cx68(0x1a3)+ _0x91f0[84]](_0x232cx68(0x165),_0x91f0[100]);continue;case _0x91f0[54]:var _0x232cx77=_0x232cx70[_0x232cx68(0x14d)](_0x91f0[101]+ _0x232cx68(0x17d)+ _0x232cx68(0x16e),_0x232cx71[_0x232cx72][_0x232cx68(0xe3)][_0x232cx68(0x157)])+ _0x232cx70[_0x232cx68(0x12c)];continue;case _0x91f0[60]:_0x232cx71[_0x232cx72][_0x91f0[106]+ _0x91f0[107]](_0x232cx70[_0x232cx68(0x11e)],function(){var _0x232cx78=_0x232cx68;var _0x232cx79=_0x232cx70[_0x232cx78(0x141)][_0x232cx78(0x160)](_0x91f0[42]);var _0x232cx7a=0x0;while(!![]){switch(_0x232cx79[_0x232cx7a++]){case _0x91f0[44]:var _0x232cx7b=document[_0x232cx78(0xd9)+ _0x91f0[31]](_0x232cx70[_0x232cx78(0x1a9)]);continue;case _0x91f0[45]:_0x232cx7b[_0x232cx78(0x1a3)+ _0x91f0[84]](_0x232cx70.EPlWw,_0x91f0[34]);continue;case _0x91f0[46]:this[_0x232cx78(0x128)]= _0x91f0[34];continue;case _0x91f0[48]:this[_0x232cx78(0x188)+ _0x91f0[99]](_0x232cx7b);continue;case _0x91f0[50]:_0x232cx7b[_0x232cx78(0x1a3)+ _0x91f0[84]](_0x232cx70[_0x232cx78(0xf1)],_0x91f0[44]);continue;case _0x91f0[54]:_0x232cx7b[_0x91f0[97]+ _0x91f0[84]](_0x232cx70[_0x232cx78(0x195)],_0x232cx70[_0x91f0[105]](_0x232cx70[_0x232cx78(0x14d)](_0x232cx70[_0x232cx78(0x15e)],this[_0x91f0[102]][_0x232cx78(0x157)]),_0x91f0[103]+ _0x91f0[104]+ _0x232cx78(0x1a6)));continue};break}});continue;case _0x91f0[61]:_0x232cx75[_0x232cx68(0x1a3)+ _0x91f0[84]](_0x232cx70[_0x232cx68(0x1ab)],_0x232cx70[_0x232cx68(0x150)]);continue};break}}}());var license_0x1b0d17={};license_0x1b0d17[_0x91f0[108]]= _0x91f0[109];Defer[license_0x47ae09(0xbe)](license_0x47ae09(0x18e),0x64,license_0x47ae09(0x169),null,license_0x1b0d17),license_0x47ae09(0x10b)!=  typeof infinite_scroll&& infinite_scroll[_0x91f0[111]](_0x91f0[110],function(){var _0x232cx7d=license_0x47ae09;var _0x232cx7e={};_0x232cx7e[_0x232cx7d(0x1b9)]= _0x232cx7d(0x18c);var _0x232cx7f=_0x232cx7e;var _0x232cx80={};_0x232cx80[_0x232cx7d(0xfc)]= _0x232cx7f[_0x232cx7d(0x1b9)];Defer[_0x232cx7d(0xbe)](_0x232cx7d(0x18e),0x64,_0x232cx7d(0x169),null,_0x232cx80)});const docHeight=()=>{var _0x232cx82=license_0x47ae09;var _0x232cx83={};_0x232cx83[_0x232cx82(0x130)]= _0x91f0[112];_0x232cx83[_0x232cx82(0x11f)]= _0x232cx82(0xfd);var _0x232cx84=_0x232cx83;const _0x232cx85=document[_0x91f0[113]+ _0x232cx82(0x162)](_0x232cx84[_0x232cx82(0x130)]);_0x232cx85[_0x232cx82(0xfe)][_0x232cx82(0x12d)+ _0x91f0[117]](_0x232cx84[_0x232cx82(0x11f)],window[_0x91f0[114]+ _0x91f0[115]]+ _0x91f0[116])};window[license_0x47ae09(0xc6)+ _0x91f0[107]](_0x91f0[118],docHeight);function license_0x79eb(){var _0x232cx87=[_0x91f0[119],_0x91f0[120],_0x91f0[121],_0x91f0[122],_0x91f0[123],_0x91f0[124],_0x91f0[125],_0x91f0[126],_0x91f0[127],_0x91f0[128],_0x91f0[129],_0x91f0[130],_0x91f0[131],_0x91f0[132],_0x91f0[133],_0x91f0[134],_0x91f0[135],_0x91f0[136],_0x91f0[137],_0x91f0[70],_0x91f0[138],_0x91f0[139],_0x91f0[140],_0x91f0[141],_0x91f0[108],_0x91f0[142],_0x91f0[143],_0x91f0[144],_0x91f0[145],_0x91f0[146],_0x91f0[147],_0x91f0[148],_0x91f0[149],_0x91f0[150],_0x91f0[151],_0x91f0[152],_0x91f0[153],_0x91f0[154],_0x91f0[155],_0x91f0[156],_0x91f0[157],_0x91f0[158],_0x91f0[159],_0x91f0[160],_0x91f0[161],_0x91f0[162],_0x91f0[163],_0x91f0[164],_0x91f0[112],_0x91f0[98],_0x91f0[165],_0x91f0[166],_0x91f0[167],_0x91f0[168],_0x91f0[169],_0x91f0[170],_0x91f0[171],_0x91f0[172],_0x91f0[173],_0x91f0[174],_0x91f0[175],_0x91f0[176],_0x91f0[177],_0x91f0[178],_0x91f0[179],_0x91f0[180],_0x91f0[181],_0x91f0[182],_0x91f0[33],_0x91f0[85],_0x91f0[183],_0x91f0[184],_0x91f0[185],_0x91f0[186],_0x91f0[187],_0x91f0[188],_0x91f0[189],_0x91f0[190],_0x91f0[191],_0x91f0[192],_0x91f0[193],_0x91f0[14],_0x91f0[194],_0x91f0[195],_0x91f0[196],_0x91f0[79],_0x91f0[197],_0x91f0[198],_0x91f0[199],_0x91f0[200],_0x91f0[201],_0x91f0[202],_0x91f0[203],_0x91f0[204],_0x91f0[205],_0x91f0[206],_0x91f0[207],_0x91f0[208],_0x91f0[209],_0x91f0[210],_0x91f0[211],_0x91f0[212],_0x91f0[213],_0x91f0[214],_0x91f0[215],_0x91f0[216],_0x91f0[217],_0x91f0[218],_0x91f0[219],_0x91f0[220],_0x91f0[221],_0x91f0[222],_0x91f0[223],_0x91f0[224],_0x91f0[225],_0x91f0[226],_0x91f0[227],_0x91f0[228],_0x91f0[229],_0x91f0[230],_0x91f0[231],_0x91f0[232],_0x91f0[233],_0x91f0[234],_0x91f0[56],_0x91f0[235],_0x91f0[236],_0x91f0[35],_0x91f0[237],_0x91f0[49],_0x91f0[238],_0x91f0[239],_0x91f0[39],_0x91f0[240],_0x91f0[241],_0x91f0[242],_0x91f0[243],_0x91f0[244],_0x91f0[245],_0x91f0[246],_0x91f0[247],_0x91f0[248],_0x91f0[31],_0x91f0[249],_0x91f0[250],_0x91f0[251],_0x91f0[252],_0x91f0[253],_0x91f0[254],_0x91f0[255],_0x91f0[256],_0x91f0[257],_0x91f0[258],_0x91f0[259],_0x91f0[260],_0x91f0[261],_0x91f0[262],_0x91f0[263],_0x91f0[264],_0x91f0[265],_0x91f0[266],_0x91f0[267],_0x91f0[268],_0x91f0[269],_0x91f0[270],_0x91f0[271],_0x91f0[272],_0x91f0[273],_0x91f0[109],_0x91f0[274],_0x91f0[275],_0x91f0[110],_0x91f0[276],_0x91f0[277],_0x91f0[278],_0x91f0[279],_0x91f0[280],_0x91f0[281],_0x91f0[282],_0x91f0[283],_0x91f0[284],_0x91f0[285],_0x91f0[286],_0x91f0[287],_0x91f0[288],_0x91f0[289],_0x91f0[290],_0x91f0[291],_0x91f0[292],_0x91f0[105],_0x91f0[293],_0x91f0[97],_0x91f0[294],_0x91f0[295],_0x91f0[296],_0x91f0[297],_0x91f0[298],_0x91f0[88],_0x91f0[299],_0x91f0[300],_0x91f0[81],_0x91f0[301],_0x91f0[302],_0x91f0[303],_0x91f0[304],_0x91f0[305],_0x91f0[306],_0x91f0[307],_0x91f0[308],_0x91f0[309],_0x91f0[310],_0x91f0[311],_0x91f0[312],_0x91f0[313],_0x91f0[314],_0x91f0[315],_0x91f0[316],_0x91f0[317],_0x91f0[318],_0x91f0[319],_0x91f0[320],_0x91f0[321],_0x91f0[322],_0x91f0[323],_0x91f0[324],_0x91f0[325],_0x91f0[326],_0x91f0[327],_0x91f0[328],_0x91f0[329],_0x91f0[330],_0x91f0[331],_0x91f0[332],_0x91f0[333],_0x91f0[334],_0x91f0[335],_0x91f0[336],_0x91f0[107],_0x91f0[337],_0x91f0[338],_0x91f0[339],_0x91f0[340],_0x91f0[341],_0x91f0[342],_0x91f0[343],_0x91f0[344],_0x91f0[345],_0x91f0[346],_0x91f0[347],_0x91f0[348],_0x91f0[106],_0x91f0[349],_0x91f0[350],_0x91f0[351],_0x91f0[352],_0x91f0[113],_0x91f0[353],_0x91f0[354],_0x91f0[355],_0x91f0[356],_0x91f0[357],_0x91f0[358],_0x91f0[359],_0x91f0[360],_0x91f0[361],_0x91f0[362],_0x91f0[363],_0x91f0[364],_0x91f0[365],_0x91f0[32],_0x91f0[366],_0x91f0[367],_0x91f0[368],_0x91f0[369],_0x91f0[370],_0x91f0[371],_0x91f0[372],_0x91f0[69],_0x91f0[373],_0x91f0[102]];license_0x79eb= function(){return _0x232cx87};return license_0x79eb()}docHeight();const d=document,l=localStorage,b=d[_0x91f0[113]+ license_0x47ae09(0x162)](license_0x47ae09(0x114)),m=d[_0x91f0[113]+ license_0x47ae09(0x162)](license_0x47ae09(0x154)+ _0x91f0[374]+ _0x91f0[375]),mM=d[license_0x47ae09(0xcb)+ license_0x47ae09(0x162)](license_0x47ae09(0x154)+ license_0x47ae09(0xea)+ license_0x47ae09(0x17e)+ license_0x47ae09(0xcd)),mA=d[license_0x47ae09(0xcb)+ license_0x47ae09(0x162)](license_0x47ae09(0x154)+ license_0x47ae09(0x1b6)+ license_0x47ae09(0x16d)+ license_0x47ae09(0xa6)+ license_0x47ae09(0xf3)),c=m[_0x91f0[352]+ _0x91f0[84]](license_0x47ae09(0x187)),cM=mM[license_0x47ae09(0xca)+ _0x91f0[84]](_0x91f0[269]),cA=mA[license_0x47ae09(0xca)+ _0x91f0[84]](_0x91f0[269]),iniTheme=license_0x47ae09(0x176),setTheme=(_0x232cx94)=>{var _0x232cx95=license_0x47ae09;var _0x232cx96={};_0x232cx96[_0x232cx95(0x19d)]= function(_0x232cx97,_0x232cx98){return _0x232cx97=== _0x232cx98};_0x232cx96[_0x91f0[311]]= _0x91f0[164];_0x232cx96[_0x232cx95(0xd4)]= _0x232cx95(0x187);_0x232cx96[_0x232cx95(0x192)]= _0x232cx95(0x122);_0x232cx96[_0x232cx95(0x167)]= _0x232cx95(0xb0);_0x232cx96[_0x232cx95(0x14c)]= _0x91f0[252];_0x232cx96[_0x91f0[293]]= _0x232cx95(0xe9);var _0x232cx99=_0x232cx96;b[_0x91f0[97]+ _0x91f0[84]](_0x91f0[376],_0x232cx94);if(_0x232cx99[_0x232cx95(0x19d)](_0x232cx94,_0x232cx99[_0x232cx95(0x1b7)])){m[_0x91f0[97]+ _0x91f0[84]](_0x232cx99.MkoWc,_0x232cx99[_0x232cx95(0x192)]);mM[_0x232cx95(0x1a3)+ _0x91f0[84]](_0x232cx99[_0x232cx95(0xd4)],_0x232cx95(0x122));mA[_0x91f0[97]+ _0x91f0[84]](_0x232cx99[_0x232cx95(0xd4)],_0x232cx99.Kfrja)}else {m[_0x232cx95(0x1a3)+ _0x91f0[84]](_0x232cx99[_0x232cx95(0xd4)],c);mM[_0x91f0[97]+ _0x91f0[84]](_0x232cx99[_0x232cx95(0xd4)],cM);mA[_0x232cx95(0x1a3)+ _0x91f0[84]](_0x232cx95(0x187),cA)};switch(_0x232cx94){case _0x232cx95(0x176):l[_0x91f0[316]](_0x232cx99[_0x232cx95(0x167)],_0x232cx99[_0x232cx95(0x14c)]);break;case _0x232cx95(0x113):l[_0x232cx95(0x1bc)](_0x232cx99[_0x232cx95(0x167)],_0x232cx95(0x113));break;case _0x232cx99[_0x232cx95(0x1a2)]:l[_0x232cx95(0x1bc)](_0x232cx95(0xb0),_0x232cx99[_0x232cx95(0x1a2)]);break}},setThemeOn=()=>{var _0x232cx9a=license_0x47ae09;var _0x232cx9b={'\x6E\x51\x4D\x56\x72':_0x232cx9a(0xb0),'\x46\x47\x53\x73\x59':function(_0x232cx9c,_0x232cx9d){return _0x232cx9c(_0x232cx9d)},'\x53\x4B\x65\x4A\x73':function(_0x232cx9e,_0x232cx9f){return _0x232cx9e=== _0x232cx9f},'\x61\x6D\x51\x72\x48':_0x91f0[164],'\x69\x72\x44\x48\x55':_0x232cx9a(0x187),'\x75\x44\x4C\x6E\x7A':_0x232cx9a(0x122)};saveTheme= l[_0x232cx9a(0xd6)](_0x232cx9b[_0x232cx9a(0xdd)]);saveTheme?b[_0x232cx9a(0x1a3)+ _0x91f0[84]](_0x91f0[376],saveTheme):_0x232cx9b[_0x232cx9a(0x1ae)](setTheme,iniTheme);if(_0x232cx9b[_0x232cx9a(0x106)](saveTheme,_0x232cx9b[_0x232cx9a(0x10f)])){m[_0x91f0[97]+ _0x91f0[84]](_0x232cx9b[_0x232cx9a(0x110)],_0x232cx9a(0x122));mM[_0x232cx9a(0x1a3)+ _0x91f0[84]](_0x232cx9b[_0x232cx9a(0x110)],_0x232cx9b[_0x232cx9a(0xdb)]);mA[_0x91f0[97]+ _0x91f0[84]](_0x232cx9b[_0x232cx9a(0x110)],_0x232cx9b[_0x232cx9a(0xdb)])}else {m[_0x232cx9a(0x1a3)+ _0x91f0[84]](_0x232cx9b[_0x232cx9a(0x110)],c);mM[_0x232cx9a(0x1a3)+ _0x91f0[84]](_0x232cx9b[_0x232cx9a(0x110)],cM);mA[_0x232cx9a(0x1a3)+ _0x91f0[84]](_0x232cx9b[_0x232cx9a(0x110)],cA)}};setThemeOn() /*]]>*/</script>
      </b:includable>
        
      <!--[ CopyCode javascript ]-->
      <b:includable id='copyCodeToClipboard'>
        <script> const cCopy = &quot;<data:messages.copyToClipboard/>&quot;; /*<![CDATA[*/ eval(function(p,a,c,k,e,r){e=function(c){return(c<a?'':e(parseInt(c/a)))+((c=c%a)>35?String.fromCharCode(c+29):c.toString(36))};if(!''.replace(/^/,String)){while(c--)r[e(c)]=k[c]||e(c);k=[function(e){return r[e]}];e=function(){return'\\w+'};c=1};while(c--)if(k[c])p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c]);return p}('8 n=s;(k(a,b){8 h=s;8 t=a();1A(!![]){1B{8 13=j(h(1C))/1D*(-j(h(1E))/1F)+j(h(1G))/1H+j(h(1I))/1J+-j(h(1K))/1L+-j(h(1M))/1N+j(h(1O))/1P*(-j(h(1Q))/1R)+j(h(1S))/1T;14(13===b){1U}1V{t[\'15\'](t[\'16\']())}}1W(1X){t[\'15\'](t[\'16\']())}}}(u,1Y));C 17=18[n(1Z)+n(20)](\'\\19\\g\\1\\0\\21\\3\\i\\2\\22\\19\'+n(23));k u(){8 1a=[\'\\2\\i\\1\',\'\\4\\9\\7\\4\\P\',\'\\Q\\2\\D\\e\\4\',\'\\l\\2\\0\\3\\0\\1\',\'\\v\\R\\2\\2\\i\\3\',\'\\0\\w\\5\\E\\4\',\'\\7\\3\\3\\0\\1\\p\\0\\o\\2\',\'\\l\\24\\1b\\F\\7\\o\\1c\\1d\\4\\i\',\'\\m\\x\\S\\G\\H\\e\\5\\T\',\'\\F\\i\\1\\I\\e\\4\\G\',\'\\g\\1\\0\',\'\\2\\i\\1\\1e\\9\\9\',\'\\2\\v\\25\',\'\\g\\7\\0\\5\\1b\\1f\\1g\\26\\l\\g\',\'\\4\\1\\0\\e\\2\\0\\I\\9\\0\\27\',\'\\y\\x\\z\\m\\y\\q\\i\\28\\J\\v\\29\\2a\',\'\\m\\U\\m\\z\\K\\A\\U\\1h\\I\\1h\\V\\D\\L\',\'\\K\\m\\x\\K\\A\\x\\W\\1i\\P\\F\\w\\X\',\'\\m\\A\\M\\q\\A\\x\\q\\1\\1j\\1k\\9\\l\\o\',\'\\e\\3\\1f\',\'\\z\\z\\1l\\m\\m\\1e\\5\\W\\P\\Y\\E\',\'\\7\\3\\3\\0\\1\\Z\\p\\H\\Q\',\'\\4\\9\\7\\g\\v\\i\\e\\1\\5\',\'\\X\\R\\0\\1\\D\\Y\\0\\9\\0\\4\',\'\\e\\g\\g\\0\\3\\5\\1j\\G\\7\\9\',\'\\e\\5\\5\\I\\1i\\0\\3\\2\\Q\\7\',\'\\M\\q\\M\\M\\A\\p\\g\\w\\l\\4\\p\',\'\\T\\7\\o\\1m\\Z\',\'\\V\\J\\L\\H\\5\',\'\\1g\\l\\g\\e\\3\\1d\\4\\9\\e\\l\',\'\\K\\U\\E\\g\\5\\1k\\2b\\G\',\'\\J\\1\\7\\2\\0\\p\\0\\o\\2\',\'\\y\\y\\q\\1l\\z\\q\\y\\i\\9\\l\\S\\S\\W\',\'\\e\\L\\1c\\F\\w\'];u=k(){r 1a};r u()}k s(c,d){8 1n=u();s=k(a,b){a=a-1o;C 1p=1n[a];r 1p};r s(c,d)}17[n(2c)](10=>{8 f=n;8 N={\'\\V\\J\\L\\H\\5\':k(a,b,c){r a(b,c)},\'\\0\\w\\5\\E\\4\':f(2d),\'\\T\\7\\o\\1m\\Z\':f(2e)};14(1q[f(2f)]){C B=18[f(1o)+\'\\0\\3\\2\'](N[f(2g)]);B[f(1r)]=11;10[f(2h)+\'\\5\'](B);B[f(2i)+f(2j)](N[f(2k)],1s()=>{8 1t=f;1u N[1t(2l)](1v,10,B)})}});1s k 1v(c,d){8 6=n;8 O={};O[6(1w)]=6(2m);O[6(1x)]=k(a,b){r a+b};8 12=O;C 1y=c[\'\\X\\R\\0\\1\\D\\Y\\0\\9\\0\\4\'+6(2n)](12[6(1w)]),1z=1y[6(1r)];1u 1q[\'\\4\\9\\7\\g\\v\\i\\e\\1\\5\'][6(2o)](1z);d[6(2p)]=12[6(1x)](11,6(2q)+6(2r)+6(2s)+6(2t));2u(()=>{d[\'\\7\\3\\3\\0\\1\\p\\0\\o\\2\']=11},2v)}',62,156,'x65|x72|x74|x6e|x63|x64|_0x1e2188|x69|const|x6c|||||x61|_0x387937|x70|_0x1fd2a6|x6f|parseInt|function|x73|x31|copyCode_0x3e34f9|x78|x54|x30|return|copyCode_0x1793|_0x333480|copyCode_0x5898|x62|x44|x38|x37|x34|x36|_0x372012|let|x79|x58|x66|x68|x4d|x45|x77|x33|x47|x39|_0xabe44d|_0x5e00a2|x6b|x4c|x75|x4a|x51|x35|x67|x52|x71|x53|x48|_0x1b5f94|cCopy|_0x24456e|_0x568ab0|if|push|shift|box|document|x2e|_0x173159|x27|x4e|x20|x41|x3e|x3c|x46|x76|x43|x49|x32|x56|_0x5898d2|0x9b|_0x2db7e6|navigator|0xb5|async|_0x199279|await|cCode|0xb1|0xae|_0x3077d7|_0x32b35e|while|try|0xa1|0x1|0xb7|0x2|0xa7|0x3|0x9f|0x4|0x9d|0x5|0x9c|0x6|0xab|0x7|0x9e|0x8|0xad|0x9|break|else|catch|_0xab0de0|0x43f6a|0xa4|0xba|x3a|x28|0xbb|x3d|x29|x2f|x6d|x7a|x4f|x57|x50|0xb8|0xb3|0xb0|0xa3|0xb4|0xa5|0xa6|0xb2|0xa8|0xa9|0xb9|0xaf|0xac|0xa2|0xaa|0xb6|0xbc|0xa0|setTimeout|0x898'.split('|'),0,{})) /*]]>*/</script>
      </b:includable>
      
      <!--[ bookmarkLoad ]-->
      <b:includable id='bookmarkLoad'>
        <script>/*<![CDATA[*/ /* Bookmark With Browser Local Storage, Created by: igniel.com, Source code: https://www.igniel.com/2022/12/widget-bookmark-blog.html */ function bookmarkLoad(){ const bookmarks = {
    maxWidget: 5,
    maxAll: 100,
    emptyText: '<span class="fontM">No bookmarks found</span>',
    moreText: 'Show all',
    currentText: '<span class="fontM">You are currently on Bookmarks page</span>',
    morePage: '/p/bookmark.html',
    deleteText: '<svg class="line" viewBox="0 0 24 24"><path d="M21 5.97998C17.67 5.64998 14.32 5.47998 10.98 5.47998C9 5.47998 7.02 5.57998 5.04 5.77998L3 5.97998"/><path d="M8.5 4.97L8.72 3.66C8.88 2.71 9 2 10.69 2H13.31C15 2 15.13 2.75 15.28 3.67L15.5 4.97"/><path d="M18.85 9.14001L18.2 19.21C18.09 20.78 18 22 15.21 22H8.79002C6.00002 22 5.91002 20.78 5.80002 19.21L5.15002 9.14001"/><!--<path d="M10.33 16.5H13.66"/><path d="M9.5 12.5H14.5"/>--></svg>'

}; /* DO NOT EDIT */ !function(d) {let ignielbookmark = JSON.parse(localStorage.getItem("ignielBookmark")) || []; d.querySelector(".ignielBookmark").querySelector("label.bc").setAttribute("data-text", ignielbookmark.length); const bmCek = () => {if (ignielbookmark.length > 0) {ignielbookmark.forEach((e) => {if (d.getElementById("bm-" + e.id)) {d.getElementById("bm-" + e.id).checked = true;} }); } }; const bmRender = () => {localStorage.setItem("ignielBookmark", JSON.stringify(ignielbookmark)); d.querySelector(".ignielBookmark").querySelector("label.bc").setAttribute("data-text", ignielbookmark.length); let bmContainer = d.querySelector(".bookmark-inner"), bmContainerAll = d.querySelector(".ignielBookmarks"), bmBuild = ""; if (ignielbookmark.length > 0) {let max = bookmarks.maxWidget, more = false; if (d.location.pathname == bookmarks.morePage) {max = bookmarks.maxAll;} else {max = bookmarks.maxWidget; if (ignielbookmark.length > max) {more = true;} } ignielbookmark.slice(0, max).forEach((e) => {bmBuild += '<div class="flex" data-id="' + e.id + '"><div class="bm-thumb shrink"><a href="' + e.url + '"><img class="bm-im" loading="lazy" alt="' + e.title + '" src="' + e.img + '"></a></div><div class="bm-title grow"><a class="clamp" href="' + e.url + '" title="' + e.title + '">' + e.title + '</a></div><div class="bm-delete flex center shrink op i18" role="button">' + bookmarks.deleteText + "</div></div>"; }); bmContainer.innerHTML += "</div>"; if (d.location.pathname == bookmarks.morePage) {bmContainer.innerHTML = bookmarks.currentText; if (bmContainerAll) bmContainerAll.innerHTML = "<div class='book all flex wrap'>" + bmBuild + "</div>";} else {bmContainer.innerHTML = "<div class='book flex column'>" + bmBuild; if (more) {bmContainer.innerHTML += '<div class="more fontS"><a href="' + bookmarks.morePage + '" title="' + bookmarks.moreText + '"><span>' + bookmarks.moreText + "</span><span class='fontSm opacity'>(+" + (ignielbookmark.length - max) + ")</span></a></div>";} } } else {bmContainer && (bmContainer.innerHTML = bookmarks.emptyText); bmContainerAll && (bmContainerAll.innerHTML = bookmarks.emptyText); } bmDel(); }; const bmAdd = (a) => {ignielbookmark.push(a); bmRender();}; const bmRem = (id) => {ignielbookmark = ignielbookmark.filter((obj) => obj.id !== id); bmRender(); if (d.getElementById("bm-" + id)) {d.getElementById("bm-" + id).checked = false;} }; const bmDel = () => {const a = d.querySelectorAll(".bm-delete"); if (a.length > 0) {a.forEach((e) => {const dId = e.parentNode.getAttribute("data-id"); e.addEventListener("click", () => {bmRem(dId); }); }); } }; const ignielBookmark = () => {const a = d.querySelectorAll(".ignielBookmarkPost input"); if (a.length > 0) {a.forEach((e) => {e.addEventListener("change", () => {const bmId = e.id.split("-")[1], bmParent = e.parentNode, bookmarkItem = {id: bmId, img: bmParent.querySelector("label").getAttribute("data-img"), title: bmParent.querySelector("label").getAttribute("data-title"), url: bmParent.querySelector("label").getAttribute("data-url") }; if (ignielbookmark) {const findId = ignielbookmark.find((obj) => obj.id === bmId); if (findId) {bmRem(bmId);} else {bmAdd(bookmarkItem);} } else {bmAdd(bookmarkItem);} }); }); } }; d.location.pathname == bookmarks.morePage && bmRender(); d.querySelector(".ignielBookmark").addEventListener("click", () => {bmRender();}); d.addEventListener("scroll", () => {bmCek; ignielBookmark}); ignielBookmark(); bmCek(); }(document);} bookmarkLoad(); "undefined" != typeof infinite_scroll && infinite_scroll.on("load", function(){ bookmarkLoad(); }); /*]]>*/</script>
      </b:includable>
      
      <!--[ Post related ]-->
      <b:includable id='postRelated'>
        <div class='relatedP noJava' id='relatedPost'>
          <script>
            var labelArray = [<b:if cond='data:post.labels'><b:loop values='data:post.labels' var='label'>&quot;<data:label.name/>&quot;<b:if cond='data:label.isLast != &quot;true&quot;'>,</b:if></b:loop></b:if>];
            var relatedPostConfig = {
              homePage: &quot;<data:blog.homepageUrl.canonical/>&quot;,
            
              // Replace <data:messages.youMayLikeThesePosts/> to change Related Posts title
              widgetTitle: &quot;<h2 class='title'><b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'><data:messages.youMayLikeThesePosts/><b:else/>You might like these products</b:if></h2>&quot;,
            
              // Change the related post style, there are 4 styles available
              widgetStyle: 1,
            
              numPosts: 6,
              summaryLength: 200,
              titleLength: &quot;auto&quot;,
              thumbnailSize: 300,
              noImage: &quot;data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=&quot;,
              containerId: &quot;relatedPost&quot;,
              newTabLink: !1,
              moreText: &quot;Read more&quot;,
            
              callBack:function(){}
            }
          </script>
          <script>/*<![CDATA[*/ /*! Related Post Widget for Blogger by Taufik Nurrohman <https://github.com/taufik-nurrohman> */
!function(e,t,a){if("object"==typeof labelArray&&labelArray.length)for(var l=t.createElement("em"),i=0,s=labelArray.length;i<s;++i)l.innerHTML=labelArray[i],labelArray[i]=l.textContent;var n=(new Date).getTime(),r={widgetTitle:"<h3 class='title'>Related Posts</h3>",widgetStyle:1,homePage:"//www.jagodesain.com",numPosts:6,summaryLength:180,titleLength:"auto",thumbnailSize:300,noImage:"data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=",containerId:"relatedPost",newTabLink:!1,moreText:"Read more",callBack:function(){}};if("object"==typeof relatedPostConfig)for(var i in relatedPostConfig)r[i]=relatedPostConfig[i];r.homePage=r.homePage.replace(/\/?\?m=\d+(\&|$)|\/+$/,"");var o=function(e){var l=t.createElement("script");l.src=e,a.appendChild(l)},m=function(e){var t,a,l=e.length;if(0===l)return!1;for(;--l;)t=Math.floor(Math.random()*(l+1)),a=e[l],e[l]=e[t],e[t]=a;return e},h="object"==typeof labelArray&&labelArray.length?"/-/"+encodeURIComponent(m(labelArray)[0]):"";e["do_related_post_"+n]=function(e){var a,l,i,s,n,ct,dt,Y,M,D,MM,o=t.getElementById(r.containerId),h=m(e.feed.entry),c=r.widgetStyle,d=r.widgetTitle+'<div class="itemR type-'+c+' flex wrap scrlH" role="feed">',u=r.newTabLink?' target="_blank"':"",mm=["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];if(o){for(var p=h.length,A=0;A<r.numPosts&&A!==p;A++){l=h[A].title.$t,i="auto"!==r.titleLength&&r.titleLength<l.length?l.substring(0,r.titleLength)+"&hellip;":l,s="media$thumbnail"in h[A]&&!1!==r.thumbnailSize?h[A].media$thumbnail.url.replace(/\/s\d+(\-c)?\//,"/s"+r.thumbnailSize+"/"):r.noImage,n="summary"in h[A]&&r.summaryLength>0?h[A].summary.$t.replace(/<br *\/?>/gi," ").replace(/<.*?>/g,"").replace(/[<>]/g,"").substring(0,r.summaryLength)+"&hellip;":"",ct=h[A].category[0].term,dt=h[A].published.$t.substring(0, 29),Y=dt.substring(0,4),M=dt.substring(5,7),D=dt.substring(8,10),MM=mm[parseInt(M-1)];for(var f=0,y=h[A].link.length;f<y;f++)if("alternate"==h[A].link[f].rel){a=h[A].link[f].href;break}d+=2==c||3==c?'<article class="flex column"><div class="pI shrink"><a aria-label="Thumbnail" class="image" href="'+a+'"'+u+'><div class="mi lazy" data-style="background-image:url('+s+')"></div></a></div><div class="pC grow flex column"><div class="pH info flex fontM"><time class="time ellips opacity shrink" data-text="'+MM+' '+D+'" datetime="'+dt+'" title="Published on: '+MM+' '+D+', '+Y+'"></time><div class="label ellips cInherit"><a aria-label="Tag" data-text="'+ct+'" href="'+r.homePage+'/search/label/'+ct+'" rel="tag"></a></div></div><div class="pT cInherit"><h4 class="name"><a class="clamp" href="'+a+'"'+u+">"+i+"</a></h4></div></div></article>":4==c?'<article class="flex column shrink"><div class="pI shrink"><a aria-label="Thumbnail" class="image" href="'+a+'"'+u+'><div class="mi lazy" data-style="background-image:url('+s+')"></div></a></div><div class="pC grow flex column"><div class="pH info flex fontM"><time class="time ellips opacity shrink" data-text="'+MM+' '+D+'" datetime="'+dt+'" title="Published on: '+MM+' '+D+', '+Y+'"></time><div class="label ellips cInherit"><a aria-label="Tag" data-text="'+ct+'" href="'+r.homePage+'/search/label/'+ct+'" rel="tag"></a></div></div><div class="pT cInherit"><h4 class="name"><a class="clamp" href="'+a+'"'+u+'>'+i+'</a></h4></div><div class="pS fontM"><div class="snippet clamp opacity">'+n+"</div></div></div></article>":'<article class="flex"><div class="pI shrink"><a aria-label="Thumbnail" class="image" href="'+a+'"'+u+'><div class="mi lazy" data-style="background-image:url('+s+')"></div></a></div><div class="pC grow"><div class="pH info flex fontM"><time class="time ellips opacity shrink" data-text="'+MM+' '+D+'" datetime="'+dt+'" title="Published on: '+MM+' '+D+', '+Y+'"></time><div class="label ellips cInherit"><a aria-label="Tag" data-text="'+ct+'" href="'+r.homePage+'/search/label/'+ct+'" rel="tag"></a></div></div><div class="pT cInherit"><h4 class="name"><a class="clamp" href="'+a+'"'+u+">"+i+"</a></h4></div></div></article>"}o.innerHTML=d+="</div>",r.callBack(e)}},e["do_related_post_start_"+n]=function(e){var t,a,l=e.feed.openSearch$totalResults.$t-r.numPosts,i=(t=1,a=l>0?l:1,Math.floor(Math.random()*(a-t+1))+t);o(r.homePage+"/feeds/posts/summary"+h+"?alt=json-in-script&orderby=updated&start-index="+i+"&max-results="+r.numPosts+"&callback=do_related_post_"+n)},o(r.homePage+"/feeds/posts/summary?alt=json-in-script&orderby=updated&max-results=0&callback=do_related_post_start_"+n)}(window,document,document.getElementsByTagName("head")[0]); /*]]>*/</script>
        </div>
      </b:includable>
      
      <!--[ Post fullpage ]-->
      <b:includable id='postFullpage'>
        <script>/*<![CDATA[*/ document.getElementsByClassName('mainB')[0].classList.add('full'); /*]]>*/</script>
      </b:includable>
    </b:defaultmarkup>
    <b:defaultmarkup type='Blog, AdSense'>
      <b:includable id='defaultAdUnit'>
        <b:comment>Clear out style (needs to be a non-empty string)</b:comment>
        <b:with value='&quot;/* Done in css. */&quot;' var='style'>
          <b:include name='super.defaultAdUnit'/>
        </b:with>
      </b:includable>
    </b:defaultmarkup>
    <b:defaultmarkup type='Blog, FeaturedPost, PopularPosts'>
      <!--[ Thumbnails ]-->
      <b:includable id='snippetedPostThumbnail'>
        <div class='pI cInherit'>
          <b:class cond='(data:view.isMultipleItems and data:widget.type == &quot;Blog&quot;) or data:widget.type == &quot;FeaturedPost&quot; or data:widget.type == &quot;PopularPosts&quot;' name='shrink'/>
          <b:class cond='data:post.featuredImage.isYoutube' name='youtube'/>
          <b:class cond='!data:post.featuredImage' name='noImage'/>

          <b:tag class='thumbnail' expr:name='data:post.featuredImage ? &quot;a&quot; : &quot;div&quot;'>
            <b:attr cond='data:post.featuredImage' expr:value='data:post.url' name='href'/>
            <b:if cond='data:post.featuredImage'>
              <b:include name='postThumbnail'/>
              <b:else/>
              <b:comment>If there is no thumbnail, an empty block will be displayed</b:comment>
              <span class='img null noWrap opacity'/>
            </b:if>
          </b:tag>

          <div class='bar flexIn'>
            <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
          
            <b:if cond='data:widget.type != &quot;PopularPosts&quot;'>
              <b:comment>Add to bookmark</b:comment>
              <div class='ignielBookmarkPost tag addl'>
                <input class='hidden addb' expr:id='&quot;bm-&quot; + data:post.id' name='bookmark' type='checkbox'/>
                <label aria-label='Add bookmark' class='flex center op i16' expr:data-img='data:post.featuredImage ? resizeImage(data:post.featuredImage, 80, &quot;1:1&quot;) :  &quot;data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=&quot;' expr:data-title='data:post.title' expr:data-url='data:post.url' expr:for='&quot;bm-&quot; + data:post.id' title='Add to bookmark'>
                  <b:include name='archive-add-icon'/>
                  <b:include name='archive-tick-icon'/>
                </label>
              </div>
            </b:if>
            
            <b:comment>Comment count</b:comment>
            <b:if cond='(data:post.allowComments and data:post.numberOfComments &gt; 0) and data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
              <b:if cond='data:widgets.Blog.first.allBylineItems.comments'>
                <b:include name='commentCount'/>
              </b:if>
            </b:if>
          
            <b:comment>Product icon</b:comment>
            <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])'>
              <b:class name='product'/>
              <span class='flex center op i16 tag'><b:include name='tag-icon'/></span>
              
              <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                <span class='flex center discount'>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount10&quot; ])' name='data-text' value='-10%'/>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount20&quot; ])' name='data-text' value='-20%'/>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount30&quot; ])' name='data-text' value='-30%'/>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount40&quot; ])' name='data-text' value='-40%'/>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount50&quot; ])' name='data-text' value='-50%'/>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount60&quot; ])' name='data-text' value='-60%'/>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount70&quot; ])' name='data-text' value='-70%'/>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount80&quot; ])' name='data-text' value='-80%'/>
                  <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount90&quot; ])' name='data-text' value='-90%'/>
                </span>
              </b:if>
            </b:if>
          </div>
          
        </div>
      </b:includable>
      
      <!--[ Snippets ]-->
      <b:includable id='postSnippet'>
        <div class='pS fontM'>
          <b:class cond='!data:post.featuredImage' name='noImage'/>
          <b:class cond='data:post.title.length lt 25' name='show'/>
          
          <div class='snippet clamp'>
            <b:class cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])' name='opacity'/>
            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='prices'/>
            
            <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
              <b:eval expr='snippet(data:post.snippets.long, {length: 150, links: false, linebreaks: false})'/>
            
              <b:else/>
              <b:comment>Use this to hide image captions in article snippets</b:comment>
              <b:eval expr='snippet(data:post.body, {length: 150, links: false, linebreaks: false})'/>
            </b:if>
          </div>
        </div>
      </b:includable>
      
      <!--[ Post labels ]-->
      <b:includable id='postLabels'>
        <b:if cond='data:widgets.Blog.first.allBylineItems.labels'>
          <div class='label ellips cInherit'>
            <b:attr cond='data:post.labels' expr:value='data:widgets.Blog.first.allBylineItems.labels.label' name='data-text'/>
            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='opacity sponsor'/>
      
            <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
              <b:loop values='data:post.labels' var='label'>
                <b:if cond='data:label.name == &quot;Sponsored&quot;'>
                  <b:tag class='extL' expr:data-text='data:label.name' name='span'/>
                </b:if>
              </b:loop>
              
              <b:else/>
              <b:loop values='data:post.labels' var='label'>
                <b:if cond='data:label.name == &quot;Product&quot;'>
                  <b:tag cond='data:widget.type != &quot;PopularPosts&quot;' name='span'>
                    <b:tag expr:data-text='data:label.name' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;span&quot;'>
                      <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                      <b:attr cond='data:blog.url != data:label.url' name='rel' value='tag'/>
                      <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                    </b:tag>
                  </b:tag>
                </b:if>
              </b:loop>
      
              <b:loop index='i' values='data:post.labels' var='label'>
                <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot;, &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                
                  <b:comment><!--[ Replace data:i &lt;= 0 with data:i &lt;= 0 to display two labels ]--></b:comment>
                  <b:if cond='data:i &lt;= 0'>
                    <b:tag cond='data:widget.type != &quot;PopularPosts&quot;' name='span'>
                      <b:tag expr:data-text='data:label.name' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;span&quot;'>
                        <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                        <b:attr cond='data:blog.url != data:label.url' name='rel' value='tag'/>
                        <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                      </b:tag>
                    </b:tag>
                  </b:if>
                
                </b:if>
              </b:loop>
            </b:if>
          </div>
        </b:if>
      </b:includable>
      
      <!--[ Post title ]-->
      <b:includable id='postTitle' var='post'>
        <b:if cond='data:post.title != &quot;&quot;'>
          <div class='pT cInherit'>
            <b:tag class='name' expr:name='data:post.link or (data:post.url and data:view.url != data:post.url) ? &quot;h2&quot; : &quot;h1&quot;'>
              <b:class cond='data:view.isSingleItem' name='item'/>
              <b:attr cond='data:view.isSingleItem and data:widget.type == &quot;Blog&quot;' name='id' value='postT'/>

              <b:if cond='data:post.link or (data:post.url and data:view.url != data:post.url)'>
                <a class='clamp' expr:href='data:post.link ?: data:post.url'><data:post.title/></a>
                <b:else/>
                <data:post.title/>
              </b:if>
            </b:tag>
          </div>
        </b:if>
      </b:includable>
    </b:defaultmarkup>
    <b:defaultmarkup type='Blog'>
      <!--[ Post description ]-->
      <b:includable id='postDescription'>
        <b:if cond='data:blog.metaDescription'>
          <div class='pD opacity'><data:blog.metaDescription/></div>
        </b:if>
      </b:includable>
      
      <!--[ Post header ]-->
      <b:includable id='postHeader' var='post'>
        <div class='pH flex space-between cInherit fontM noPrint'>
          <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot;, &quot;Sponsored&quot; ])' name='tag'/>
          <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
            <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
              <b:comment>Author photo</b:comment>
              <b:if cond='data:widgets.Blog.first.allBylineItems.author'>
                <b:tag class='byline img flex center shrink' cond='data:post.author.authorPhoto.image' name='div'>
                  <b:include name='postAuthorImage'/>
                </b:tag>
              </b:if>
            </b:if>
            <div class='byline item grow'>
              <b:if cond='data:widgets.Blog.first.allBylineItems.author and data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
                <b:include name='postAuthorName'/>
              </b:if>
                
              <b:tag class='date' cond='data:widgets.Blog.first.allBylineItems.timestamp' name='span'>
                <b:include name='postTimestamps'/>
            
                <b:comment>Estimated/calculated reading time of posts</b:comment>
                <b:include name='postTimeread'/>
              </b:tag>
            </div>
          </b:if>
          
          <b:comment>Share button and bookmark</b:comment>
          <div class='byline share flex shrink'>
            <div class='ignielBookmarkPost'>
              <input class='hidden addb' expr:id='&quot;bm-&quot; + data:post.id' name='bookmark' type='checkbox'/>
              <label aria-label='Add bookmark' class='flex center opacity i20' expr:data-img='data:post.featuredImage ? resizeImage(data:post.featuredImage, 100, &quot;1:1&quot;) :  &quot;data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=&quot;' expr:data-title='data:post.title' expr:data-url='data:post.url' expr:for='&quot;bm-&quot; + data:post.id' title='Add to bookmark'>
                <b:include name='archive-add-icon'/>
                <b:include name='archive-tick-icon'/>
              </label>
            </div>
            
            <!--<b:if cond='data:post.shareUrl and data:widgets.Blog.first.allBylineItems.share'>-->
              <b:include name='postShareButton'/>
            <!--</b:if>-->
          </div>
        </div>
      </b:includable>
      
      <!--[ Post authors ]-->
      <b:includable id='aboutPostAuthor'>
        <div class='authors flex fontM'>
          <div class='img shrink'>
            <b:include name='postAuthorImage'/>
          </div>
          <div class='name'>
            <b:tag class='namei hidden' cond='data:post.author.aboutMe.length &gt; 200' id='forAuthor' name='input' type='checkbox'/>
            
            <bdi class='m cInherit' expr:data-text='data:post.author.name' expr:data-write='data:messages.postedBy'/>
            <div class='d flex'>
              <div class='clamp'><b:eval expr='data:post.author.aboutMe snippet {links: true, linebreaks: true}'/></div>
              <b:tag aria-label='Show description' class='shrink' expr:data-text='data:messages.showAll' for='forAuthor' name='label'/>
            </div>
            
          </div>
        </div>
      </b:includable>
      
      <!--[ Post empty ]-->
      <b:includable id='noContentPlaceholder'>
        <b:if cond='data:posts.empty'>
          <b:comment>You can replace <data:messages.noResultsFound/> with <data:messages.theresNothingHere/></b:comment>
          <div class='n'><data:messages.noResultsFound/>...</div>
        </b:if>
      </b:includable>
    </b:defaultmarkup>
    <b:defaultmarkup type='Blog, FeaturedPost'>
      <!--[ Meta rich results ]-->
      <b:includable id='postMeta' var='post'>
        <b:include data='post' name='postMetadataJSON'/>
      </b:includable>
      <b:includable id='postMetadataJSON'>
        <script type='application/ld+json'>
          {
            &quot;@context&quot;: &quot;http://schema.org&quot;,
            &quot;@type&quot;: &quot;BlogPosting&quot;,
            &quot;mainEntityOfPage&quot;: {
              &quot;@type&quot;: &quot;WebPage&quot;,
              &quot;@id&quot;: &quot;<data:post.url.canonical.jsonEscaped/>&quot;
            },
            &quot;headline&quot;: &quot;<data:post.title.jsonEscaped/>&quot;,
            &quot;description&quot;: &quot;<b:eval expr='snippet(data:post.snippets.long, {length: 250, links: false, linebreaks: false, ellipsis: true }).jsonEscaped'/>&quot;,
            <b:if cond='data:view.isSingleItem'>&quot;articleBody&quot;: &quot;<b:eval expr='snippet(data:post.body, {links: false, linebreaks: false, ellipsis: true}).jsonEscaped'/>&quot;,</b:if>
            &quot;datePublished&quot;: &quot;<data:post.date.iso8601.jsonEscaped/>&quot;,
            &quot;dateModified&quot;: &quot;<data:post.lastUpdated.iso8601.jsonEscaped/>&quot;,
            <b:include data='post' name='postMetadataJSONImage'/><b:include data='post' name='postMetadataJSONPublisher'/>
            &quot;author&quot;: {
              &quot;@type&quot;: &quot;Person&quot;,
              &quot;name&quot;: &quot;<data:post.author.name.jsonEscaped/>&quot;,
          
              /* Get Blogger profile url, otherwise homepage url will be shown */
              &quot;url&quot;: &quot;<b:if cond='data:post.author.profileUrl'><data:post.author.profileUrl.jsonEscaped/><b:else/><data:blog.homepageUrl.jsonEscaped/></b:if>&quot;,
          
              /* Get Blogger profile photo, otherwise Blogger logo will be shown */
              &quot;image&quot;: &quot;<b:if cond='data:post.author.authorPhoto.image'><data:post.author.authorPhoto.image.jsonEscaped/><b:else/>https://www.blogger.com/img/blogger_logo_round_35.png</b:if>&quot;
            }
          }
        </script>
      </b:includable>
      <b:includable id='postMetadataJSONImage'>
        &quot;image&quot;: {
          &quot;@type&quot;: &quot;ImageObject&quot;,
        
          /* Get the first image, otherwise no default image will be shown */
          &quot;url&quot;: &quot;<b:eval expr='(data:post.featuredImage ? resizeImage(data:post.featuredImage, 1200, &quot;1200:630&quot;) : &quot;https://1.bp.blogspot.com/-E250bQMM8tk/XomH5DdorOI/AAAAAAAAPY8/SCYwi79WjckWC8wHKK7OblI82BpT9JquACNcBGAsYHQ/s1600/jagotheme-img.png&quot;)'/>&quot;,
          &quot;height&quot;: <b:eval expr='data:post.featuredImage ? 630 : 420'/>,
          &quot;width&quot;: 1200
        },
      </b:includable>
      <b:includable id='postMetadataJSONPublisher'>
        &quot;publisher&quot;: {
          &quot;@type&quot;: &quot;Organization&quot;,
          &quot;name&quot;: &quot;<data:blog.title.escaped/>&quot;,
          &quot;logo&quot;: {
            &quot;@type&quot;: &quot;ImageObject&quot;,
            &quot;url&quot;: &quot;https://1.bp.blogspot.com/-50s1RMWV7jI/X8OaYjJcMiI/AAAAAAAAQK4/sWcpbaP0Sq0hsW473Vnb8AyBvYvdSQEPwCNcBGAsYHQ/s0/jd-logo.png&quot;,
            &quot;width&quot;: 297,
            &quot;height&quot;: 45
          }
        },
      </b:includable>
    </b:defaultmarkup>
    <b:defaultmarkup type='FeaturedPost, PopularPosts'>
      <b:includable id='blogThisShare'/>
      <b:includable id='bylineByName' var='byline'/>
      <b:includable id='bylineRegion' var='regionItems'/>
      <b:includable id='commentsLink'/>
      <b:includable id='commentsLinkIframe'/>
      <b:includable id='emailPostIcon'/>
      <b:includable id='facebookShare'/>
      <b:includable id='footerBylines'/>
      <b:includable id='googlePlusShare'/>
      <b:includable id='headerByline'/>
      <b:includable id='linkShare'/>
      <b:includable id='otherSharingButton'/>
      <b:includable id='platformShare'/>
      <b:includable id='postAuthor'/>
      <b:includable id='postCommentsLink'/>
      <b:includable id='postLocation'/>
      <b:includable id='postReactions'/>
      <b:includable id='postShareButtons'/>
      <b:includable id='postTimestamp'/>
      <b:includable id='sharingButton'/>
      <b:includable id='sharingButtonContent'/>
      <b:includable id='sharingButtons'/>
      <b:includable id='sharingButtonsMenu'/>
      <b:includable id='sharingPlatformIcon'/>
      <b:includable id='snippetedPostByline'/>
      <b:includable id='snippetedPostTitle'>
        <!--[ Post title ]-->
        <b:include data='post' name='postTitle'/>
      </b:includable>
    </b:defaultmarkup>
    <b:defaultmarkup type='FeaturedPost'>
      <b:includable id='main' var='this'>
        <b:if cond='data:title != &quot;&quot;'>
          <h2 class='title'><data:title/></h2>
        </b:if>
        <b:include name='snippetedPosts'/>
      </b:includable>
      <b:includable id='postFooter' var='post'>
        <b:tag class='pF items flex space-between fontM cInherit' name='div'>
          <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
          
          <b:comment>post Footer in MultipleItems page</b:comment>
          <b:include cond='data:post.labels none (label =&gt; label.name in [&quot;Sponsored&quot; ])' name='postTimestamps'/>
            
          <b:comment><!--[ Jumplink / read more link ]--></b:comment>
          <b:include data='post' name='postJumpLink'/>
          
        </b:tag>
      </b:includable>
      <b:includable id='postJumpLink' var='post'>
        <a class='jump jumpLink shrink' expr:aria-label='data:blog.jumpLinkMessage' expr:data-text='data:blog.jumpLinkMessage' expr:href='data:post.url'>
          <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
        </a>
      </b:includable>
      <b:includable id='snippetedPostContent'>
        <!--[ Post thumbnails ]-->
        <b:include cond='data:this.postDisplay.showFeaturedImage and data:post.featuredImage' name='snippetedPostThumbnail'/>
        
        <!--[ Post content (title, body, etc.) ]-->
        <b:tag class='pC grow' name='div'>
          <b:class name='flex column'/>
          
          <b:include name='postInfo'/>
          <b:include cond='data:this.postDisplay.showTitle' name='snippetedPostTitle'/>
          <b:include cond='data:this.postDisplay.showSnippet' data='post' name='postSnippet'/>
          
          <!--[ Post footer ]-->
          <b:include cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])' data='post' name='postFooter'/>
          
          <!--[ Meta rich results ]-->
          <b:include data='post' name='postMeta'/>
        </b:tag>
      </b:includable>
      <b:includable id='snippetedPosts'>
        <div class='itemP featured' role='feed'>
          <!-- Don't render the post that we're currently already looking at. -->
          <b:loop values='data:posts filter (p =&gt; p.id != data:view.postId)' var='post'>
            <article class='i flex wrap'>
              <b:class cond='data:view.isMultipleItems and !data:post.featuredImage' name='noImage'/>
              <b:class cond='!data:widgets.Blog.first.allBylineItems.timestamp' name='noTime'/>
              <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
              <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
              <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='shop'/>
              
              <b:include name='snippetedPostContent'/>
            </article>
          </b:loop>
        </div>
      </b:includable>
    </b:defaultmarkup>
    <b:defaultmarkup type='PopularPosts'>
      <b:includable id='main' var='this'>
        <b:include name='widget-title'/>
        <b:include name='snippetedPosts'/>
      </b:includable>
      <b:includable id='postJumpLink' var='post'/>
      <b:includable id='postHeaders' var='post'>
        <b:tag class='pH info flex cInherit fontM' name='div'>
          <b:include cond='data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='postTimestamps'/>
                              
          <b:comment>Show label or Sponsored</b:comment>
          <b:include cond='data:post.labels' name='postLabels'/>
        </b:tag>
      </b:includable>
      <b:includable id='snippetedPostContent'>
        <!--[ Post thumbnails ]-->
        <b:include cond='data:i == 0 and (data:this.postDisplay.showFeaturedImage and data:post.featuredImage)' name='snippetedPostThumbnail'/>
        
        <div class='pC flex'>
          <div class='pB'>
            <!--[ Post header ]-->
            <b:include data='post' name='postHeaders'/>
            
            <b:include cond='data:this.postDisplay.showTitle' name='snippetedPostTitle'/>
            <b:include cond='data:this.postDisplay.showSnippet and data:i == 0' data='post' name='postSnippet'/>
          </div>
        </div>
      </b:includable>
      <b:includable id='snippetedPosts'>
        <div class='itemP popular flex column' role='feed'>
          <!-- Don't render the post that we're currently already looking at. -->
          <b:loop index='i' values='data:posts filter (p =&gt; p.id != data:view.postId)' var='post'>
            <article class='i'>
              <b:class cond='data:i == 0 and (data:this.postDisplay.showFeaturedImage and !data:post.featuredImage)' name='noImage'/>
              <b:class cond='data:i == 0 and (data:this.postDisplay.showFeaturedImage and data:post.featuredImage)' name='most flex column'/>
              <b:class cond='!data:widgets.Blog.first.allBylineItems.timestamp' name='noTime'/>
              <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
              <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
              <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='shop'/>
              
              <b:include name='snippetedPostContent'/>
            </article>
          </b:loop>
        </div>
      </b:includable>
    </b:defaultmarkup>
    <b:defaultmarkup type='Label'>
      <b:includable id='cloud'>
        <b:if cond='data:this.showFreqNumbers'>
          <span class='count fontSm shrink' expr:data-text='&quot;(&quot; + data:label.count + &quot;)&quot;'/>
        </b:if>
      </b:includable>
      <b:includable id='content'>
        <div class='itemL cInherit fontS'>
          <b:class expr:name='data:this.display'/>
          <b:tag class='labi hidden' cond='data:labels.length &gt; (7 + 1)' expr:id='data:widget.instanceId + &quot;-in&quot;' name='input' type='checkbox'/>
          
          <b:tag class='lab flex wrap' name='div'>
            <b:class cond='data:this.display == &quot;list&quot;' name='list'/>
            <b:loop index='list' values='data:labels' var='label'>
              <b:if cond='data:label.name != &quot;Discount10&quot; and data:label.name != &quot;Discount20&quot; and data:label.name != &quot;Discount30&quot; and data:label.name != &quot;Discount40&quot; and data:label.name != &quot;Discount50&quot; and data:label.name != &quot;Discount60&quot; and data:label.name != &quot;Discount70&quot; and data:label.name != &quot;Discount80&quot; and data:label.name != &quot;Discount90&quot;'>
                <div>
                  <b:class cond='data:this.display != &quot;list&quot;' expr:name='&quot;s-&quot; + data:label.cssSize'/>
                
                  <b:comment>Showing only 8 lists</b:comment>
                  <b:class cond='data:list &lt;= 7' name='s'/>
      
                  <b:tag class='link flex space-between' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;div&quot;'>
                    <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                    <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                    <b:class cond='data:this.display != &quot;list&quot;' name='c'/>
            
                    <b:comment>Activate to remove background color</b:comment>
                    <b:class cond='data:this.display == &quot;list&quot;' name='noBg'/>
                        
                    <span class='name ellips'><data:label.name/></span>
                  
                    <b:if cond='data:this.display == &quot;list&quot;'>
                      <b:include name='list'/>
                      <b:else/>
                      <b:include name='cloud'/>
                    </b:if>
                  
                  </b:tag>
                
                </div>
              </b:if>
            </b:loop>
          </b:tag>
          
          <b:comment>Show/hide label</b:comment>
          <b:tag aria-label='Show all labels' class='flexIn baseline' cond='data:labels.length &gt; (7 + 1)' expr:data-hide='data:messages.showLess' expr:data-length='&quot;(+&quot; + (data:labels.length - (7 + 1)) + &quot;)&quot;' expr:data-show='data:messages.showAll' expr:for='data:widget.instanceId + &quot;-in&quot;' name='label' role='button'/>
          
        </div>
      </b:includable>
      <b:includable id='list'>
        <span class='count fontSm flexIn center shrink op i16'>
          <b:attr cond='data:this.showFreqNumbers' expr:value='data:label.count' name='data-text'/>
          <b:include name='tag-right-icon'/>
        </span>
      </b:includable>
    </b:defaultmarkup>
  </b:defaultmarkups>
 
  <b:if cond='!data:view.isError'>
    <b:if cond='data:view.isPost'>
      <script>/*<![CDATA[*/ /* Table of Content, Credit: blustemy.io/creating-a-table-of-contents-in-javascript */
class TableOfContents { constructor({ from, to }) { this.fromElement = from; this.toElement = to; this.headingElements = this.fromElement.querySelectorAll("h1, h2, h3, h4, h5, h6"); this.tocElement = document.createElement("div"); }; getMostImportantHeadingLevel() { let mostImportantHeadingLevel = 6; for (let i = 0; i < this.headingElements.length; i++) { let headingLevel = TableOfContents.getHeadingLevel(this.headingElements[i]); mostImportantHeadingLevel = (headingLevel < mostImportantHeadingLevel) ? headingLevel : mostImportantHeadingLevel; } return mostImportantHeadingLevel; }; static generateId(headingElement) { return headingElement.textContent.replace(/\s+/g, "_"); }; static getHeadingLevel(headingElement) { switch (headingElement.tagName.toLowerCase()) { case "h1": return 1; case "h2": return 2; case "h3": return 3; case "h4": return 4; case "h5": return 5; case "h6": return 6; default: return 1; } }; generateToc() { let currentLevel = this.getMostImportantHeadingLevel() - 1, currentElement = this.tocElement; for (let i = 0; i < this.headingElements.length; i++) { let headingElement = this.headingElements[i], headingLevel = TableOfContents.getHeadingLevel(headingElement), headingLevelDifference = headingLevel - currentLevel, linkElement = document.createElement("a"); if (!headingElement.id) { headingElement.id = TableOfContents.generateId(headingElement); } linkElement.href = `#${headingElement.id}`; linkElement.textContent = headingElement.textContent; if (headingLevelDifference > 0) { for (let j = 0; j < headingLevelDifference; j++) { let listElement = document.createElement("ol"), listItemElement = document.createElement("li"); listElement.appendChild(listItemElement); currentElement.appendChild(listElement); currentElement = listItemElement; } currentElement.appendChild(linkElement); } else { for (let j = 0; j < -headingLevelDifference; j++) { currentElement = currentElement.parentNode.parentNode; } let listItemElement = document.createElement("li"); listItemElement.appendChild(linkElement); currentElement.parentNode.appendChild(listItemElement); currentElement = listItemElement; } currentLevel = headingLevel; } this.toElement.appendChild(this.tocElement.firstChild); } } /*]]>*/</script>
    </b:if>
    <b:if cond='data:blog.analyticsAccountNumber'>
      <!-- Google tag (gtag.js) -->
      <script async='async' expr:src='&quot;https://www.googletagmanager.com/gtag/js?id=&quot; + data:blog.analyticsAccountNumber'/>
      <script>window.dataLayer = window.dataLayer || []; function gtag(){dataLayer.push(arguments);} gtag(&#39;js&#39;, new Date()); gtag(&#39;config&#39;, &#39;<data:blog.analyticsAccountNumber/>&#39;);</script>
    </b:if>
  </b:if>
  
  <script type='application/ld+json'>
  {
    &quot;@context&quot;: &quot;https://schema.org&quot;,
    &quot;@type&quot;: &quot;WebSite&quot;,
    &quot;url&quot;: &quot;<data:blog.homepageUrl.canonical/>&quot;,
    &quot;name&quot;: &quot;<data:blog.title/>&quot;,
    &quot;alternateName&quot;: &quot;<data:blog.title/>&quot;,
    &quot;potentialAction&quot;: {
      &quot;@type&quot;: &quot;SearchAction&quot;,
      &quot;target&quot;: &quot;<data:blog.homepageUrl.canonical/>search?q={search_term_string}&quot;,
      &quot;query-input&quot;: &quot;required name=search_term_string&quot;
    }
  }
  </script>
  
  <!--[ </head> close ]-->
  &lt;!--<head/><b:if cond='!data:blog.adsenseClientId'>--&gt;&lt;/head&gt;</b:if>

  <!--[ <body> open ]-->
  <body>
    <b:attr name='id' value='nB'/>
    <b:attr name='data-theme' value='default'/>
    <b:class name='nJs'/>
    
    <b:class name='nB'/>
    <b:class cond='data:view.url == data:blog.homepageUrl.canonical path &quot;search&quot;' name='blog'/>
    <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
    <b:class cond='data:view.isMultipleItems' name='index'/>
    <b:class cond='data:view.isMultipleItems != data:view.isHomepage' name='multi'/>
    <b:class cond='data:view.isHomepage' name='home'/>
    <b:class cond='data:view.isSingleItem' name='item'/>
    <b:class cond='data:view.isPage' name='page'/>
    <b:class cond='data:view.isPost' name='post'/>
    <b:class cond='data:view.isError' name='error'/>
    <b:class cond='data:view.isPreview' name='preview'/>
    
    <b:comment><!--[ Activate the tag below so that the menu is always open ]--></b:comment>
    <!--<b:class name='openMenu'/>-->
    
    <b:comment><!--[ Show only one grid column in Mobile ]--></b:comment>
    <!--<b:class cond='data:view.isMultipleItems' name='oneGrid'/>-->
    
    <b:comment><!--[ Header sticky in mobile ]--></b:comment>
    <!--<b:class name='stickyHeader'/>-->
      
    <b:if cond='!data:view.isError'>      
      <b:comment><!--[ to activate the function ]--></b:comment>
      <input class='navi hidden' id='forNav' type='checkbox'/>
      
      <!--[ Wrapper ]-->
      <b:tag class='mainW' name='div'>
        
        <!--[ Header ]-->
        <header class='mainH flex cInherit noPrint'>
          
          <div class='headL flex shrink'>
            
            <b:if cond='!data:view.isLayoutMode'>
              <b:comment>Menu button</b:comment>
              <div class='headi menu flex center'>
                <label aria-label='Open menu' class='mc fc ic op i20' for='forNav'><b:include name='menu-2-icon'/></label>
              </div>
            </b:if>
            
            <b:comment>Header widget</b:comment>
            <b:section class='headT notranslate' id='header-title' maxwidgets='1' showaddelement='false'>
              <b:widget id='Header1' locked='true' title='veaverise (رأس الصفحة)' type='Header' version='2' visible='true'>
                <b:widget-settings>
                  <b:widget-setting name='displayUrl'/>
                  <b:widget-setting name='displayHeight'>0</b:widget-setting>
                  <b:widget-setting name='sectionWidth'>790</b:widget-setting>
                  <b:widget-setting name='useImage'>false</b:widget-setting>
                  <b:widget-setting name='shrinkToFit'>false</b:widget-setting>
                  <b:widget-setting name='imagePlacement'>BEHIND</b:widget-setting>
                  <b:widget-setting name='displayWidth'>0</b:widget-setting>
                </b:widget-settings>
                <b:includable id='main' var='this'>
                  <b:include cond='data:imagePlacement in {&quot;REPLACE&quot;, &quot;BEFORE_DESCRIPTION&quot;}' name='image'/>
                  <b:include cond='data:imagePlacement not in {&quot;REPLACE&quot;, &quot;BEFORE_DESCRIPTION&quot;}' name='title'/>
                  <b:include cond='data:imagePlacement != &quot;REPLACE&quot;' name='description'/>
                  <b:include cond='data:imagePlacement == &quot;BEHIND&quot;' name='behindImageStyle'/>
                </b:includable>
                <b:includable id='behindImageStyle'>
                  <b:if cond='data:sourceUrl'>
                    <b:include cond='data:this.image' data='{image: data:this.image, selector: &quot;.Header&quot;}' name='responsiveImageStyle'/>
                  </b:if>
                </b:includable>
                <b:includable id='description'>
                  <b:if cond='data:this.description'>
                    <div class='headD hidden'><data:this.description/></div>
                  </b:if>
                </b:includable>
                <b:includable id='image'>
                  <!-- Header image -->
                  <a expr:href='data:blog.homepageUrl'>
                    <img class='lazy' expr:alt='data:title' expr:data-src='resizeImage(data:sourceUrl, 200)' expr:height='data:height' expr:width='data:width' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs='/>
                  </a>
                  <b:include cond='data:this.imagePlacement == &quot;REPLACE&quot;' name='title'/>
                </b:includable>
                <b:includable id='title'>
                  <!-- Header title -->
                  <div class='headI'>
                    <b:class cond='data:this.imagePlacement == &quot;REPLACE&quot;' name='hidden'/>
                    <b:tag class='headN' expr:name='!data:view.isSingleItem ? &quot;h1&quot; : &quot;h2&quot;'>
                      <b:class cond='data:this.description' name='d'/>
                        
                      <b:tag class='headt ellips' expr:name='!data:view.isHomepage ? &quot;a&quot; : &quot;span&quot;'>
                        <b:attr cond='!data:view.isHomepage' expr:value='data:blog.homepageUrl' name='href'/>
                        <data:title/>
                      </b:tag>
                    </b:tag>
                  </div>
                </b:includable>
              </b:widget>
            </b:section>
          </div>
          
          <div class='headR flex shrink'>
            
            <b:comment>Search input</b:comment>
            <b:section class='headS' id='header-search' maxwidgets='2' showaddelement='false'>
              <b:widget id='BlogSearch1' locked='true' title='e.g. Typography' type='BlogSearch' version='2' visible='true'>
                <b:includable id='main'>
                      <b:include name='content'/>
                    </b:includable>
                <b:includable id='content'>
                  <b:include name='searchForm'/>
                </b:includable>
                <b:includable id='searchForm'>
                  <form class='srh fontM' expr:action='data:blog.searchUrl'>
                    <b:attr cond='!data:view.isPreview' name='target' value='_top'/>
                    <b:include name='urlParamsAsFormInput'/>
                      
                    <input autocomplete='off' class='shI bgInherit fontBa ellips' expr:aria-label='data:messages.searchThisBlog' expr:placeholder='data:view.search.query ? data:view.search.query.escaped : data:title' id='forSearch' minlength='3' name='q' required='required' type='search'/>
                    
                    <b:include name='searchSubmit'/>
                    
                    <b:comment>Clear button</b:comment>
                    <button aria-label='Clear' class='b bu bgInherit flex center invisible' data-text='Clear' type='reset'>
                      <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                    </button>
                  </form>
                </b:includable>
                <b:includable id='searchSubmit'>
                  <label class='b ba bgInherit flex center op i18' for='forSearch'>
                    <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                    <b:include name='search-icon'/>
                  </label>
                </b:includable>
              </b:widget>
            </b:section>
            
            <b:comment>Header icon</b:comment>
            <div class='headB'>
              <b:if cond='!data:view.isLayoutMode'>
                <b:comment>important to activate the function</b:comment>
                <b:tag class='setI hidden' id='forSettings' name='input' type='checkbox'/>
                <b:tag class='proI hidden' id='forUsers' name='input' type='checkbox'/>
                <b:tag class='darkI hidden' id='forDark' name='input' type='checkbox'/>
                <input class='bookI hidden' id='forBook' type='checkbox'/>
              </b:if>
              
              <b:section id='header-icon' maxwidgets='3' showaddelement='false'>
                <b:widget id='TextList00' locked='true' title='Header icon' type='TextList' version='2' visible='true'>
                  <b:widget-settings>
                    <b:widget-setting name='shownum'/>
                    <b:widget-setting name='sorting'>NONE</b:widget-setting>
                    <b:widget-setting name='item-2'>Bookmark</b:widget-setting>
                    <b:widget-setting name='item-1'>Dark</b:widget-setting>
                    <b:widget-setting name='item-0'>Search</b:widget-setting>
                  </b:widget-settings>
                  <b:includable id='main'>
                    <div class='headi flex'>
                      <b:include name='content'/>
                    </div>
                  </b:includable>
                  <b:includable id='content'>
                    <b:loop values='data:items' var='item'>
                      <!--[ Search button(mobile) ]-->
                      <b:if cond='data:item == &quot;Search&quot;'>
                        <label class='sc ic op i20' expr:aria-label='data:item' for='forSearch'>
                          <b:include name='search-icon'/>
                        </label>
                      </b:if>
                    </b:loop>
                  
                    <b:loop index='icon' values='data:items' var='item'>
                      
                      <!--[ Dark ]-->
                      <b:if cond='data:item == &quot;Dark&quot;'>
                        <label class='dc fc ic op i20 noJava' expr:aria-label='data:item' for='forDark'>
                          <b:include name='moon-n-sun-2-icon'/>
                        </label>
                        
                        <!--[ Bookmark ]-->
                        <b:elseif cond='data:item == &quot;Bookmark&quot;'/>
                        <!-- Web Blog Bookmark With Browser Local Storage, Created by: igniel.com, Source code: https://www.igniel.com/2022/12/widget-bookmark-blog.html -->
                        <div class='ignielBookmark ibook'>
                          <label class='bc fc ic op i20 noJava' data-text='0' expr:aria-label='data:item' for='forBook'>
                            <b:include name='frame-icon'/>
                          </label>
                        </div>
                        
                        <!--[ Bag/Cart ]-->
                        <b:elseif cond='data:item == &quot;Cart&quot;'/>
                        <div class='cc ic op i20 noJava' expr:aria-label='data:item'>
                          <b:include name='bag-icon'/>
                        </div>
                        
                        <!--[ Translate ]-->
                        <b:elseif cond='data:item == &quot;Translate&quot;'/>
                        <div class='tc ic op i20 noJava' expr:aria-label='data:item'>
                          <b:include name='translate-icon'/>
                        </div>
                        
                      </b:if>
                      
                    </b:loop>
                    
                    <b:loop values='data:items' var='item'>
                      <!--[ Settings ]-->
                      <b:if cond='data:item == &quot;Settings&quot;'>
                        <label class='st fc ic op i20' expr:aria-label='data:item' for='forSettings'>
                          <b:include name='category-2-icon'/>
                        </label>
                      </b:if>
                    </b:loop>
                    
                    <b:loop values='data:items' var='item'>
                      <!--[ Profile ]-->
                      <b:if cond='data:item == &quot;Profile&quot;'>
                        <label class='pc fc ic op i20' expr:aria-label='data:item' for='forUsers'>
                          <b:include name='profile-circle-icon'/>
                        </label>
                      </b:if>
                    </b:loop>
                  </b:includable>
                </b:widget>
              </b:section>
              
              <b:comment>Settings</b:comment>
              <div class='settB'>
                <b:section id='settings-id' showaddelement='true'>
                  <b:widget id='TextList11' locked='true' title='Setting icon' type='TextList' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='shownum'/>
                      <b:widget-setting name='sorting'>NONE</b:widget-setting>
                      <b:widget-setting name='item-1'>Bookmark</b:widget-setting>
                      <b:widget-setting name='item-0'>Dark</b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <div class='iSett ipopUp invisible'>
                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                        
                        <div class='setti flex'>
                          <b:include name='content'/>
                        </div>
                      </div>
                    </b:includable>
                    <b:includable id='content'>                  
                      <b:loop index='setting' values='data:items' var='item'>
                      <div>
                        <!--[ Dark ]-->
                        <b:if cond='data:item == &quot;Dark&quot;'>
                          <label class='dc ic op i20 noJava' expr:aria-label='data:item' for='forDark'>
                            <b:include name='moon-n-sun-2-icon'/>
                          </label>
                        
                          <!--[ Bookmark ]-->
                          <b:elseif cond='data:item == &quot;Bookmark&quot;'/>
                          <div class='ignielBookmark ibook'>
                            <label class='bc fc ic op i20 noJava' data-text='0' expr:aria-label='data:item' for='forBook'>
                              <b:include name='frame-icon'/>
                            </label>
                          </div>
                        
                          <!--[ Bag/Cart ]-->
                          <b:elseif cond='data:item == &quot;Cart&quot;'/>
                          <div class='ic op i20 noJava' expr:aria-label='data:item'>
                            <b:include name='bag-icon'/>
                          </div>
                        
                          <!--[ Translate ]-->
                          <b:elseif cond='data:item == &quot;Translate&quot;'/>
                          <div class='ic op i20 noJava' expr:aria-label='data:item'>
                            <b:include name='translate-icon'/>
                          </div>
                        
                          <b:comment>Your custome setting is here</b:comment>
                        </b:if>
                        </div>
                      </b:loop>
                    </b:includable>
                  </b:widget>
                  <b:widget id='LinkList00' locked='true' title='Appearance' type='LinkList' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='shownum'>4</b:widget-setting>
                      <b:widget-setting name='link-3'>Setting applies to this browser only</b:widget-setting>
                      <b:widget-setting name='sorting'>NONE</b:widget-setting>
                      <b:widget-setting name='text-1'>Dark</b:widget-setting>
                      <b:widget-setting name='link-1'>custom_text</b:widget-setting>
                      <b:widget-setting name='text-0'>System</b:widget-setting>
                      <b:widget-setting name='link-2'>custom_text</b:widget-setting>
                      <b:widget-setting name='text-3'>Text</b:widget-setting>
                      <b:widget-setting name='link-0'>custom_text</b:widget-setting>
                      <b:widget-setting name='text-2'>Light</b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <b:include name='content'/>
                    </b:includable>
                    <b:includable id='content'>
                      <div class='iTheme ipopUp flex column invisible noJava'>
                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                      
                        <b:comment>Heading</b:comment>
                        <label class='h flexIn fontS opacity i14' expr:aria-label='data:title' expr:data-text='data:title' for='forDark'>
                          <b:if cond='data:blog.languageDirection != &quot;rtl&quot;'>
                            <b:include name='arrow-left-1-icon'/>
                            <b:else/>
                            <b:include name='arrow-right-1-icon'/>
                          </b:if>
                        </label>
                      
                        <div class='inn flex fontS'>
                          <b:loop index='theme' values='data:links' var='link'>
                            <b:if cond='data:theme &lt;= 3'>
                              <span class='fontM' expr:data-text='data:link.name'>
                                <b:class cond='data:link.name == &quot;Dark&quot;' name='D'/>
                                <b:class cond='data:link.name == &quot;Light&quot;' name='L'/>
                                <b:class cond='data:link.name == &quot;System&quot;' name='A'/>
                                <b:class cond='data:link.name == &quot;Text&quot;' name='opacity'/>
                                <b:attr cond='data:link.name == &quot;Dark&quot;' name='onclick' value='setTheme(&apos;dark&apos;)'/>
                                <b:attr cond='data:link.name == &quot;Light&quot;' name='onclick' value='setTheme(&apos;light&apos;)'/>
                                <b:attr cond='data:link.name == &quot;System&quot;' name='onclick' value='setTheme(&apos;default&apos;)'/>
                                <b:attr cond='data:link.name != &quot;Text&quot;' name='role' value='button'/>
                                <b:attr cond='data:link.name != &quot;Text&quot;' expr:value='data:link.name' name='aria-label'/>
                                <b:attr cond='data:link.target != &quot;#&quot; and data:link.target != &quot;custom_text&quot;' expr:value='data:link.target' name='data-text'/>
                                
                                <b:if cond='data:link.name == &quot;System&quot;'>
                                  <span class='i flex a'>
                                    <span class='c'>
                                      <span class='k flex column'>
                                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                        <i class='t flex'/>
                                        <i class='p flex column'/>
                                      </span>
                                    </span>
                                    <span class='c rev'>
                                      <span class='k flex column'>
                                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                        <i class='t flex'/>
                                        <i class='p flex column'/>
                                      </span>
                                    </span>
                                  </span>
                              
                                  <b:elseif cond='data:link.name == &quot;Dark&quot;'/>
                                  <span class='i rev flex d'>
                                    <span class='c'>
                                      <span class='k flex column'>
                                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                        <i class='t flex'/>
                                        <i class='p flex column'/>
                                      </span>
                                    </span>
                                  </span>
                              
                                  <b:elseif cond='data:link.name == &quot;Light&quot;'/>
                                  <span class='i flex l'>
                                    <span class='c'>
                                      <span class='k flex column'>
                                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                        <i class='t flex'/>
                                        <i class='p flex column'/>
                                      </span>
                                    </span>
                                  </span>
                                </b:if>
                              </span>
                            </b:if>
                          </b:loop>
                        </div>
                      </div>
                    </b:includable>
                  </b:widget>
                  <b:widget id='TextList22' locked='true' title='Bookmark' type='TextList' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='shownum'/>
                      <b:widget-setting name='sorting'>NONE</b:widget-setting>
                      <b:widget-setting name='item-0'>Your bookmarks</b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <b:include name='content'/>
                    </b:includable>
                    <b:includable id='content'>
                      <b:loop index='i' values='data:items' var='item'>
                        <b:if cond='data:i &lt;= 0'>
                          <div class='iBook ipopUp flex column invisible noJava'>
                            <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                      
                            <b:comment>Heading</b:comment>
                            <label class='h flexIn fontS opacity i14' expr:aria-label='data:item' expr:data-text='data:item' for='forBook'>
                              <b:if cond='data:blog.languageDirection != &quot;rtl&quot;'>
                                <b:include name='arrow-left-1-icon'/>
                                <b:else/>
                                <b:include name='arrow-right-1-icon'/>
                              </b:if>
                            </label>
                        
                            <div class='bookmark-inner flex column'>
                              <b:comment>Load bookmark list</b:comment>
                              <div class='loading flex center fontM opacity i18' expr:data-text='data:messages.loading'>
                                <svg viewBox='0 0 50 50' x='0px' y='0px'><path d='M25.251,6.461c-10.318,0-18.683,8.365-18.683,18.683h4.068c0-8.071,6.543-14.615,14.615-14.615V6.461z'><animateTransform attributeName='transform' attributeType='xml' dur='0.6s' from='0 25 25' repeatCount='indefinite' to='360 25 25' type='rotate'/></path></svg>
                              </div>
                            </div>
                      
                          </div>
                        </b:if>
                      </b:loop>
                    </b:includable>
                  </b:widget>
                </b:section>
              </div>
            </div>
            
          </div>
          
        </header>
          
        <div class='mainN flex'>
          <!--[ Nav ]-->
          <div class='mainL noPrint shrink'>
            <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
            <div class='leftW flex cInherit'>
              <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
              <div class='leftN'>
              
                <b:section class='leftM' id='Left-menu' maxwidgets='2' showaddelement='false'>
                  <b:widget id='HTML000' locked='true' title='Main Menu' type='HTML' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='content'><![CDATA[<!--[ You can only edit this widget from HTML theme ]-->]]></b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <ul class='leftNav flex column noList' itemscope='itemscope' itemtype='https://schema.org/SiteNavigationElement'>
                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                        
                        <!--[ Homepage menu ]-->
                        <li class='leftC'>
                          <b:tag class='a flex op i20' expr:name='!data:view.isHomepage ? &quot;a&quot; : &quot;div&quot;'>
                            <b:class cond='data:view.isHomepage' name='home'/>
                            <b:attr cond='!data:view.isHomepage' expr:value='data:messages.home' name='aria-label'/>
                            <b:attr cond='!data:view.isHomepage' expr:value='data:blog.homepageUrl.canonical' name='href'/>
                            <b:attr cond='!data:view.isHomepage' name='itemprop' value='url'/>
                              
                            <!--[ icon ]-->
                            <b:include name='home-icon'/>
                            
                            <!--[ name ]-->
                            <div class='n text'>
                              <span>
                                <b:attr cond='!data:view.isHomepage' name='itemprop' value='name'/>
                                
                                <b:comment><!--[ Replace <data:messages.home/> tag with the text you want ]--></b:comment>
                                <data:messages.home/>
                              </span>
                            </div>
                          </b:tag>
                        </li>
                      
                        <!--[ Dropdown ]-->
                        <li class='leftC dr'>
                          <b:comment><!--[ Add open='' attribute to keep the menu open ]--></b:comment>
                          <b:tag name='details'>
                            <b:tag class='a flex noWrap op i20' name='summary'>
                              <!--[ icon ]-->
                              <b:include name='folder-2-icon'/>
                          
                              <!--[ name ]-->
                              <b:tag class='flexIn center grow text' name='span'>
                                <span>Sub menu</span>
                                <b:include name='arrow-down-1-icon'/>
                              </b:tag>
                            </b:tag>
                            
                            <ul class='n'>
                              <b:comment><!--[ Change attribute href='#' to add url ]--></b:comment>
                              <li itemprop='name'>
                                <a href='#' itemprop='url'>
                                  <span>Sub-menu 01</span>
                                </a>
                              </li>
                              <li itemprop='name'>
                                <a href='#' itemprop='url'>
                                  <span>Sub-menu 02</span>
                                </a>
                              </li>
                            
                              <li class='m' data-text='Mini heading' itemprop='name'>
                                <a href='#' itemprop='url'>
                                  <span>Sub-menu 03</span>
                                </a>
                              </li>
                              <li itemprop='name'>
                                <a href='#' itemprop='url'>
                                  <span>Sub-menu 04</span>
                                </a>
                              </li>
                            </ul>
                            
                          </b:tag>
                        </li>
                      
                        <!--[ Dropdown ]-->
                        <li class='leftC dr br'>
                          <b:comment><!--[ Add open='' attribute to keep the menu open ]--></b:comment>
                          <b:tag name='details'>
                            <b:tag class='a flex noWrap op i20' name='summary'>
                              <!--[ icon ]-->
                              <b:include name='folder-2-icon'/>
                          
                              <!--[ name ]-->
                              <b:tag class='flexIn center grow text' name='span'>
                                <span>Sub menu</span>
                                <b:include name='arrow-down-1-icon'/>
                              </b:tag>
                            </b:tag>
                            
                            <ul class='n'>
                              <b:comment><!--[ Change attribute href='#' to add url ]--></b:comment>
                              <li itemprop='name'>
                                <a href='#' itemprop='url'>
                                  <span>Sub-menu 05</span>
                                </a>
                              </li>
                              <li itemprop='name'>
                                <a href='#' itemprop='url'>
                                  <span>Sub-menu 06</span>
                                </a>
                              </li>
                            
                              <li itemprop='name'>
                                <a href='#' itemprop='url'>
                                  <span>Sub-menu 07</span>
                                </a>
                              </li>
                              <li itemprop='name'>
                                <a href='#' itemprop='url'>
                                  <span>Sub-menu 08</span>
                                </a>
                              </li>
                            </ul>
                            
                          </b:tag>
                        </li>
                          
                        <!--[ Standar menu ]-->
                        <li class='leftC'>
                          <b:comment>Change attribute href= to add url</b:comment>
                          <a aria-label='About' class='a flex op i20' href='#' itemprop='url'>
                            <!--[ icon ]-->
                            <b:include name='profile-2user-icon'/>
                            
                            <!--[ name ]-->
                            <div class='n text'>
                              <span itemprop='name'>About</span>
                            </div>
                          </a>
                        </li>
                          
                        <!--[ Standar menu ]-->
                        <li class='leftC br'>
                          <b:comment>Change attribute href= to add url</b:comment>
                          <a aria-label='Contact' class='a flex op i20' href='#' itemprop='url'>
                            <!--[ icon ]-->
                            <b:include name='sms-edit-icon'/>
                            
                            <!--[ name ]-->
                            <div class='n text'>
                              <span itemprop='name'>Contact</span>
                            </div>
                          </a>
                        </li>
                          
                        <!--[ Standar menu ]-->
                        <li class='leftC'>
                          <b:comment>Change attribute href= to add url</b:comment>
                          <a aria-label='Custom menu' class='a flex op i20' href='#' itemprop='url'>
                            <!--[ icon ]-->
                            <b:include name='folder-2-icon'/>
                            
                            <!--[ name ]-->
                            <div class='n noWrap text'>
                              <span class='extL' itemprop='name'>Custom menu</span>
                            </div>
                          </a>
                        </li>
                          
                        <!--[ Standar menu ]-->
                        <li class='leftC'>
                          <b:comment>Change attribute href= to add url</b:comment>
                          <a aria-label='Custom menu' class='a flex op i20' href='#' itemprop='url'>
                            <!--[ icon ]-->
                            <b:include name='folder-2-icon'/>
                            
                            <!--[ name ]-->
                            <div class='n noWrap text'>
                              <span class='new' itemprop='name'>Custom menu</span>
                            </div>
                          </a>
                        </li>
                          
                        <!--[ Standar menu ]-->
                        <li class='leftC'>
                          <b:comment>Change attribute href= to add url</b:comment>
                          <a aria-label='Custom menu' class='a flex op i20' href='#' itemprop='url'>
                            <!--[ icon ]-->
                            <b:include name='folder-2-icon'/>
                            
                            <!--[ name ]-->
                            <div class='n noWrap text'>
                              <span class='free' itemprop='name'>Custom menu</span>
                            </div>
                          </a>
                        </li>
                      </ul>
                    </b:includable>
                  </b:widget>
                  <b:widget id='LinkList000' locked='true' title='Main Menu (alternative)' type='LinkList' version='2' visible='false'>
                    <b:widget-settings>
                      <b:widget-setting name='link-3'>#</b:widget-setting>
                      <b:widget-setting name='sorting'>NONE</b:widget-setting>
                      <b:widget-setting name='text-1'>About_</b:widget-setting>
                      <b:widget-setting name='link-1'>#</b:widget-setting>
                      <b:widget-setting name='text-0'>Home</b:widget-setting>
                      <b:widget-setting name='link-2'>#</b:widget-setting>
                      <b:widget-setting name='text-3'>Custom menu</b:widget-setting>
                      <b:widget-setting name='link-0'>custom_text</b:widget-setting>
                      <b:widget-setting name='text-2'>Contact__</b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <b:include name='content'/>
                    </b:includable>
                    <b:includable id='content'>
                      <ul class='leftNav flex column noList' itemscope='itemscope' itemtype='https://schema.org/SiteNavigationElement'>
                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                        
                        <b:loop values='data:links' var='link'>
                          <b:if cond='data:link.name == &quot;Home&quot;'>
                            <!--[ Homepage menu ]-->
                            <li class='leftC'>
                              <b:tag class='a flex op i20' expr:name='!data:view.isHomepage ? &quot;a&quot; : &quot;div&quot;'>
                                <b:class cond='data:view.isHomepage' name='home'/>
                                <b:attr cond='!data:view.isHomepage' expr:value='data:messages.home' name='aria-label'/>
                                <b:attr cond='!data:view.isHomepage' expr:value='data:blog.homepageUrl.canonical' name='href'/>
                                <b:attr cond='!data:view.isHomepage' name='itemprop' value='url'/>
                              
                                <!--[ icon ]-->
                                <b:include name='home-icon'/>
                            
                                <!--[ name ]-->
                                <div class='n text'>
                                  <span>
                                    <b:attr cond='!data:view.isHomepage' name='itemprop' value='name'/>
                                
                                    <b:if cond='data:link.target != &quot;#&quot; and data:link.target != &quot;custom_text&quot;'>
                                      <data:link.target/>
                                      <b:else/>
                                      <data:link.name/>
                                    </b:if>
                                  </span>
                                </div>
                              </b:tag>
                            </li>
                          </b:if>
                        </b:loop>
                        
                        <b:loop values='data:links' var='link'>
                          <b:if cond='data:link.name != &quot;Home&quot;'>
                            <li class='leftC'>
                              <a aria-label='About' class='a flex op i20' expr:href='data:link.target' itemprop='url'>
                                <!--[ icon ]-->
                                <b:if cond='data:link.name == &quot;About&quot;'>
                                  <b:include name='profile-2user-icon'/>
                                  
                                  <b:elseif cond='data:link.name == &quot;Contact&quot;'/>
                                  <b:include name='sms-edit-icon'/>
                                  
                                  <b:else/>
                                  <b:include name='folder-2-icon'/>
                                </b:if>
                            
                                <!--[ name ]-->
                                <div class='n text'>
                                  <span itemprop='name'><data:link.name/></span>
                                </div>
                              </a>
                            </li>
                          </b:if>
                        </b:loop>
                        
                      </ul>
                    </b:includable>
                  </b:widget>
                </b:section>
              
                <b:section class='leftP' id='Left-profile' maxwidgets='2' showaddelement='false'>
                  <b:widget id='Profile1' locked='false' title='Contributors' type='Profile' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='showaboutme'>true</b:widget-setting>
                      <b:widget-setting name='showlocation'>true</b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main' var='this'>
                      <b:include name='content'/>
                    </b:includable>
                    <b:includable id='authorProfileImage'>
                      <b:tag class='av' name='span'>
                        <span class='avatar flex center shrink bgAlt' expr:data-style='&quot;background-image: url(&quot; + resizeImage(data:authorPhoto.image,35) + &quot;)&quot;'>
                          <b:class cond='!data:view.isPreview' name='lazy'/>
                          <b:class cond='data:team' name='n'/>
                          <b:attr cond='data:view.isPreview' expr:value='&quot;background-image: url(&quot; + resizeImage(data:authorPhoto.image,35) + &quot;)&quot;' name='style'/>
                        </span>
                        <noscript>
                          <span class='avatar flex center bgAlt' expr:style='&quot;background-image: url(&quot; + resizeImage(data:authorPhoto.image,35) + &quot;)&quot;'>
                            <b:class cond='data:team' name='n'/>
                          </span>
                        </noscript>
                      </b:tag>
                    </b:includable>
                    <b:includable id='content'>
                      <b:tag class='proP hidden' id='forProfile' name='input' type='checkbox'/>
                      
                      <!--[ Profile: icon ]-->
                      <div class='profileIcon leftC flex'>
                        <b:class expr:name='data:team ? &quot;team&quot; : &quot;solo&quot;'/>
                        <label class='a flexIn fc' for='forProfile'>
                          <b:if cond='data:team'>
                            <b:comment>Profile Teams</b:comment>
                            <b:loop index='team' values='data:authors' var='author'>
                              <b:if cond='data:team &lt;= 2'>
                                <b:include data='author' name='profileImage'/>
                                
                              </b:if>
                            </b:loop>
                            <b:tag class='n p fontS opacity' cond='data:authors.length &gt; (2 + 1)' expr:data-text='&quot;+&quot; + (data:authors.length - (2 + 1))' name='span'/>
                            <b:if cond='!data:blog.isMobileRequest'>
                              <span class='avi flex center op i20'><b:include name='profile-circle-icon'/></span>
                            </b:if>
                            
                            <b:else/>
                            <b:comment>Profile individual</b:comment>
                            <b:include name='profileImage'/>
                            <b:comment>Name and location</b:comment>
                            <span class='n flex column'>
                              <span class='fontS'>
                                <b:include name='userProfileNameOnly'/>
                              </span>
                              <b:include cond='data:showlocation and data:location != &quot;&quot;' name='userLocation'/>
                            </span>
                          </b:if>
                        </label>
                      </div>
                      
                      <!--[ Profile: pop-up ]-->
                      <div class='profilePop invisible'>
                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                        <b:class expr:name='data:team ? &quot;team&quot; : &quot;solo&quot;'/>
                        <b:class cond='!data:team' name='flex'/>
                        <b:if cond='data:team'>
                          <b:comment>Profile Teams</b:comment>
                          <b:include name='teamProfile'/>
                          
                          <b:else/>
                          <b:comment>Profile Individual</b:comment>
                          <div class='proTeam'>
                            <div class='h flex'>
                              <b:include name='profileImage'/>
                              <b:comment>Name and location</b:comment>
                              <div class='n flex column'>
                                <div class='fontS'>
                                  <b:comment>Replace with userProfileLink to show profile with link</b:comment>
                                  <b:include name='userProfileNameOnly'/>
                                </div>
                                <b:include cond='data:showlocation and data:location != &quot;&quot;' name='userLocation'/>
                              </div>
                            </div>
                          
                            <div class='d'>
                              <b:include cond='data:aboutme != &quot;&quot;' name='userProfileText'/>
                            </div>
                          </div>
                        </b:if>
                      </div>
                    </b:includable>
                    <b:includable id='defaultProfileImage'>
                      <b:tag class='av' name='span'>
                        <span class='avatar flex center shrink bgAlt op i14'>
                          <b:class cond='data:team' name='n'/>
                          <b:include name='user-icon'/>
                        </span>
                      </b:tag>
                    </b:includable>
                    <b:includable id='profileImage'>
                      <b:if cond='data:authorPhoto.image'>
                        <b:include name='authorProfileImage'/>
                        <b:else/>
                        <b:include name='defaultProfileImage'/>
                      </b:if>
                    </b:includable>
                    <b:includable id='teamProfile'>
                      <b:tag class='proT hidden' cond='data:authors.length &gt; (3 + 1)' expr:id='data:widget.instanceId + &quot;-in&quot;' name='input' type='checkbox'/>
                      
                      <div class='proTeam flex column fontM fontBa'>
                        <b:loop index='team' values='data:authors' var='author'>
                          <div class='team'>
                            <b:comment>Showing only 4 team</b:comment>
                            <b:class cond='data:team &lt;= 3' name='s'/>
                            
                            <b:comment>Replace with teamProfileLink to show profile with link</b:comment>
                            <b:include data='author' name='teamProfileName'/>
                          </div>
                        </b:loop>
                      </div>
        
                      <b:tag aria-label='Show all contributors' class='fontM' cond='data:authors.length &gt; (3 + 1)' expr:data-text='data:messages.showAll + &quot; (+&quot; + (data:authors.length - (3 + 1)) + &quot;)&quot;' expr:for='data:widget.instanceId + &quot;-in&quot;' name='label'/>
                    </b:includable>
                    <b:includable id='teamProfileLink'>
                      <a class='flex' expr:aria-label='data:display-name' expr:data-text='data:display-name' expr:href='data:userUrl' rel='noreferrer' target='_blank'>
                        <b:include name='profileImage'/>
                      </a>
                    </b:includable>
                    <b:includable id='teamProfileName'>
                      <div class='flex' expr:data-text='data:display-name'>
                        <b:include name='profileImage'/>
                      </div>
                    </b:includable>
                    <b:includable id='userLocation'>
                      <span class='location fontSm opacity ellips' expr:data-text='data:location'/>
                    </b:includable>
                    <b:includable id='userProfile'><!--[ removed ]--></b:includable>
                    <b:includable id='userProfileData'><!--[ removed ]--></b:includable>
                    <b:includable id='userProfileImage'><!--[ removed ]--></b:includable>
                    <b:includable id='userProfileInfo'><!--[ removed ]--></b:includable>
                    <b:includable id='userProfileLink'>
                      <a class='name extL' expr:href='data:userUrl' expr:title='data:messages.viewMyCompleteProfile' rel='author noreferrer' target='_blank'>
                        <bdi><data:displayname/></bdi>
                      </a>
                    </b:includable>
                    <b:includable id='userProfileNameOnly'>
                      <span class='name'><bdi><data:displayname/></bdi></span>
                    </b:includable>
                    <b:includable id='userProfileText'>
                      <b:tag class='proT hidden' cond='data:aboutme.length &gt; 200' expr:id='data:widget.instanceId + &quot;-in&quot;' name='input' type='checkbox'/>
    
                      <div class='t fontS'>
                        <b:class cond='data:aboutme.length &gt; 200' name='clamp'/>
      
                        <b:comment>Add length: 200, To limit the number of characters appearing</b:comment>
                        <b:eval expr='data:aboutme snippet {links: true, linebreaks: true}'/>
                      </div>
                      <b:tag class='fontS' cond='data:aboutme.length &gt; 200' expr:data-text='data:messages.showAll' expr:for='data:widget.instanceId + &quot;-in&quot;' name='label'/>
                    </b:includable>
                    <b:includable id='viewProfileLink'><!--[ removed ]--></b:includable>
                  </b:widget>
                </b:section>
              
                <div class='leftF leftC hidden fontM'>
                  <label aria-label='Close menu' class='flexIn' for='forNav'/>
                </div>
                
              </div>
            </div>
          </div>
        
          <div class='mainR flex column grow'>
            
            <!--[ Content ]-->
            <div class='mainC'>
              
              <b:comment><!--[ Widget: Notify ]--></b:comment>
              <b:section class='notify fontM noPrint' id='notif-widget' maxwidgets='1' showaddelement='false'>
                <b:widget id='HTML0' locked='true' title='Notification' type='HTML' version='2' visible='false'>
                  <b:widget-settings>
                    <b:widget-setting name='content'><![CDATA[Lorem ipsum dolor sit amet, consectetur adipiscing elit. <a href='#'>Test link</a>]]></b:widget-setting>
                  </b:widget-settings>
                  <b:includable id='main'>
                    <b:tag class='maxC' name='div'>
                      <details open=''>
                        <summary class='n flex center'>
                          <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                          <span class='c' data-text='Close'/>
                        </summary>
                        <div class='p flex center'>
                          <div>
                            <data:content/>
                          </div>
                        </div>
                      </details>
                    </b:tag>
                  </b:includable>
                </b:widget>
              </b:section>
           
              <b:tag class='maxC' name='div'>
                
                <b:comment><!--[ Widget: Billboard ad ]--></b:comment>
                <b:section class='mainAd noPrint' id='billboard-ad' maxwidgets='2' showaddelement='true'>
                  <b:widget id='HTML91' locked='true' title='Ads under header' type='HTML' version='2' visible='false'>
                    <b:widget-settings>
                      <b:widget-setting name='content'/>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <b:if cond='data:content != &quot;&quot;'>
                        <data:content/>
                          
                        <b:else/>
                        <!--[ Blank ad ]-->
                        <div class='adB' expr:data-text='data:messages.adsGoHere'/>
                      </b:if>
                    </b:includable>
                  </b:widget>
                </b:section>
                
                <b:comment><!--[ Widget: Main and Sidebar ]--></b:comment>
                <div class='mainB flex wrap'>
                  
                  <main class='blogB grow'>
                    <b:class cond='data:view.isPost' name='item'/>
                    <b:class cond='data:view.isPage' name='static'/>
                    
                    <b:comment>Custom Slider</b:comment>
                    <b:if cond='data:view.isHomepage'>
                      <div class='slideB scrlH fontM noPrint'>
                        <b:section class='slider flex' id='slider-widget' maxwidgets='4' showaddelement='false'>
                          <b:widget id='Image1' locked='true' title='Slider image 1' type='Image' version='2' visible='true'>
                            <b:widget-settings>
                              <b:widget-setting name='displayUrl'>https://1.bp.blogspot.com/-yMSpgmjn390/YF1Q5CvGIcI/AAAAAAAAQlg/59LxYemhlyEbbhqlpdfypu5OXRav4t-JgCNcBGAsYHQ/s1600/slider-1-min.png</b:widget-setting>
                              <b:widget-setting name='displayHeight'>648</b:widget-setting>
                              <b:widget-setting name='sectionWidth'>453</b:widget-setting>
                              <b:widget-setting name='shrinkToFit'>false</b:widget-setting>
                              <b:widget-setting name='displayWidth'>1600</b:widget-setting>
                              <b:widget-setting name='link'/>
                              <b:widget-setting name='caption'>coba ahh</b:widget-setting>
                            </b:widget-settings>
                            <b:includable id='main'>
                              <b:include name='content'/>
                            </b:includable>
                            <b:includable id='content'>
                              <div class='item'>
                                <b:if cond='!data:view.isPreview'>
                                  <b:tag class='img' expr:data-style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;'>
                                    <b:class name='lazy'/>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                            
                                  <b:else/>
                                  <b:tag class='img' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;' expr:style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;'>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                                </b:if>
                          
                                <b:comment>If javascript was disabled</b:comment>
                                <noscript>
                                  <b:tag class='img' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;' expr:style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;'>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                                </noscript>
                              </div>
                            </b:includable>
                          </b:widget>
                          <b:widget id='Image2' locked='true' title='Slider image 2' type='Image' version='2' visible='true'>
                            <b:widget-settings>
                              <b:widget-setting name='displayUrl'>https://1.bp.blogspot.com/-dGxoQ9YQYsM/YF1Q71CYmII/AAAAAAAAQlo/0scDqH__JA87HT6QpRcFZt9Y7CucundjQCNcBGAsYHQ/s1600/slider-2-min.png</b:widget-setting>
                              <b:widget-setting name='displayHeight'>648</b:widget-setting>
                              <b:widget-setting name='sectionWidth'>453</b:widget-setting>
                              <b:widget-setting name='shrinkToFit'>false</b:widget-setting>
                              <b:widget-setting name='displayWidth'>1600</b:widget-setting>
                              <b:widget-setting name='link'/>
                              <b:widget-setting name='caption'/>
                            </b:widget-settings>
                            <b:includable id='main'>
                              <b:include name='content'/>
                            </b:includable>
                            <b:includable id='content'>
                              <div class='item'>
                                <b:if cond='!data:view.isPreview'>
                                  <b:tag class='img' expr:data-style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;'>
                                    <b:class name='lazy'/>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                            
                                  <b:else/>
                                  <b:tag class='img' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;' expr:style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;'>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                                </b:if>
                          
                                <b:comment>If javascript was disabled</b:comment>
                                <noscript>
                                  <b:tag class='img' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;' expr:style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;'>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                                </noscript>
                              </div>
                            </b:includable>
                          </b:widget>
                          <b:widget id='Image3' locked='true' title='Slider image 3' type='Image' version='2' visible='true'>
                            <b:widget-settings>
                              <b:widget-setting name='displayUrl'>https://1.bp.blogspot.com/-vK7BQxXeYnk/YF1Q9MVgZ8I/AAAAAAAAQls/OanP_Tl4sd4616Y1RaD2JPA_UOWtMkDAQCNcBGAsYHQ/s1600/slider-3-min.png</b:widget-setting>
                              <b:widget-setting name='displayHeight'>648</b:widget-setting>
                              <b:widget-setting name='sectionWidth'>453</b:widget-setting>
                              <b:widget-setting name='shrinkToFit'>false</b:widget-setting>
                              <b:widget-setting name='displayWidth'>1600</b:widget-setting>
                              <b:widget-setting name='link'/>
                              <b:widget-setting name='caption'/>
                            </b:widget-settings>
                            <b:includable id='main'>
                              <b:include name='content'/>
                            </b:includable>
                            <b:includable id='content'>
                              <div class='item'>
                                <b:if cond='!data:view.isPreview'>
                                  <b:tag class='img' expr:data-style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;'>
                                    <b:class name='lazy'/>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                            
                                  <b:else/>
                                  <b:tag class='img' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;' expr:style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;'>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                                </b:if>
                          
                                <b:comment>If javascript was disabled</b:comment>
                                <noscript>
                                  <b:tag class='img' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;' expr:style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;'>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                                </noscript>
                              </div>
                            </b:includable>
                          </b:widget>
                          <b:widget id='Image4' locked='true' title='Slider image 4' type='Image' version='2' visible='true'>
                            <b:widget-settings>
                              <b:widget-setting name='displayUrl'>https://1.bp.blogspot.com/-Q_BGkGuukLE/YF1Q67reH4I/AAAAAAAAQlk/jXe6LIyIjkkNpJu7ShtztoUWV4JylmCkgCNcBGAsYHQ/s1600/slider-4-min.png</b:widget-setting>
                              <b:widget-setting name='displayHeight'>648</b:widget-setting>
                              <b:widget-setting name='sectionWidth'>453</b:widget-setting>
                              <b:widget-setting name='shrinkToFit'>false</b:widget-setting>
                              <b:widget-setting name='displayWidth'>1600</b:widget-setting>
                              <b:widget-setting name='link'>https://theme.jagodesain.com</b:widget-setting>
                              <b:widget-setting name='caption'/>
                            </b:widget-settings>
                            <b:includable id='main'>
                              <b:include name='content'/>
                            </b:includable>
                            <b:includable id='content'>
                              <div class='item'>
                                <b:if cond='!data:view.isPreview'>
                                  <b:tag class='img' expr:data-style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;'>
                                    <b:class name='lazy'/>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                            
                                  <b:else/>
                                  <b:tag class='img' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;' expr:style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;'>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                                </b:if>
                          
                                <b:comment>If javascript was disabled</b:comment>
                                <noscript>
                                  <b:tag class='img' expr:name='data:link ? &quot;a&quot; : &quot;div&quot;' expr:style='&quot;background-image: url(&quot; + data:sourceUrl + &quot;)&quot;'>
                                    <b:attr cond='data:link' expr:value='data:link' name='href'/>
                                    <b:attr cond='data:link' expr:value='data:title' name='aria-label'/>
                                    <b:if cond='data:caption'><span class='cap'><data:caption/></span></b:if>
                                  </b:tag>
                                </noscript>
                              </div>
                            </b:includable>
                          </b:widget>
                        </b:section>
                          
                        <div class='slideI flex center i12'>
                          <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                          <span class='i'/>
                          <span class='i'/>
                          <span class='i'/>
                          <span class='i'/>
                  
                          <b:comment>Play/pause indicator</b:comment>
                          <b:include name='playPause-icon'/>
                        </div>
                      </div>
                    </b:if>
              
                    <b:section class='flex column' cond='data:view.isHomepage' id='top-widget' showaddelement='true'>
                      <b:widget cond='!data:view.isPreview' id='HTML92' locked='true' title='Ads go here' type='HTML' version='2' visible='false'>
                        <b:widget-settings>
                          <b:widget-setting name='content'/>
                        </b:widget-settings>
                        <b:includable id='main'>
                          <b:if cond='data:content != &quot;&quot;'>
                            <data:content/>
                        
                            <b:else/>
                            <!--[ Blank ad ]-->
                            <div class='adB' expr:data-text='data:messages.adsGoHere'/>
                          </b:if>
                        </b:includable>
                      </b:widget>
                      <b:widget cond='data:view.isHomepage' id='FeaturedPost1' locked='true' title='Pinned Post' type='FeaturedPost' version='2' visible='false'>
                        <b:widget-settings>
                          <b:widget-setting name='showSnippet'>true</b:widget-setting>
                          <b:widget-setting name='showPostTitle'>true</b:widget-setting>
                          <b:widget-setting name='postId'>0</b:widget-setting>
                          <b:widget-setting name='showFirstImage'>true</b:widget-setting>
                          <b:widget-setting name='useMostRecentPost'>true</b:widget-setting>
                        </b:widget-settings>
                        <b:includable id='main' var='this'>
                          <b:if cond='data:title != &quot;&quot;'>
                            <h2 class='title'><data:title/></h2>
                          </b:if>
                          <b:include name='snippetedPosts'/>
                        </b:includable>
                        <b:includable id='blogThisShare'/>
                        <b:includable id='bylineByName' var='byline'/>
                        <b:includable id='bylineRegion' var='regionItems'/>
                        <b:includable id='commentsLink'/>
                        <b:includable id='commentsLinkIframe'/>
                        <b:includable id='emailPostIcon'/>
                        <b:includable id='facebookShare'/>
                        <b:includable id='footerBylines'/>
                        <b:includable id='googlePlusShare'/>
                        <b:includable id='headerByline'/>
                        <b:includable id='linkShare'/>
                        <b:includable id='otherSharingButton'/>
                        <b:includable id='platformShare'/>
                        <b:includable id='postAuthor'/>
                        <b:includable id='postCommentsLink'/>
                        <b:includable id='postFooter' var='post'>
                          <b:tag class='pF items flex space-between fontM cInherit' name='div'>
                            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
                            
                            <b:comment>post Footer in MultipleItems page</b:comment>
                            <b:include cond='data:post.labels none (label =&gt; label.name in [&quot;Sponsored&quot; ])' name='postTimestamps'/>
                              
                            <b:comment><!--[ Jumplink / read more link ]--></b:comment>
                            <b:include data='post' name='postJumpLink'/>
                            
                          </b:tag>
                        </b:includable>
                        <b:includable id='postJumpLink' var='post'>
                          <a class='jump jumpLink shrink' expr:aria-label='data:blog.jumpLinkMessage' expr:data-text='data:blog.jumpLinkMessage' expr:href='data:post.url'>
                            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
                          </a>
                        </b:includable>
                        <b:includable id='postLabels'>
                          <b:if cond='data:widgets.Blog.first.allBylineItems.labels'>
                            <div class='label ellips cInherit'>
                              <b:attr cond='data:post.labels' expr:value='data:widgets.Blog.first.allBylineItems.labels.label' name='data-text'/>
                              <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='opacity sponsor'/>
      
                              <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
                                <b:loop values='data:post.labels' var='label'>
                                  <b:if cond='data:label.name == &quot;Sponsored&quot;'>
                                    <b:tag class='extL' expr:data-text='data:label.name' name='span'/>
                                  </b:if>
                                </b:loop>
              
                                <b:else/>
                                <b:loop values='data:post.labels' var='label'>
                                  <b:if cond='data:label.name == &quot;Product&quot;'>
                                    <b:tag cond='data:widget.type != &quot;PopularPosts&quot;' name='span'>
                                      <b:tag expr:data-text='data:label.name' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;span&quot;'>
                                        <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                                        <b:attr cond='data:blog.url != data:label.url' name='rel' value='tag'/>
                                        <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                                      </b:tag>
                                    </b:tag>
                                  </b:if>
                                </b:loop>
      
                                <b:loop index='i' values='data:post.labels' var='label'>
                                  <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot;, &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                
                                    <b:comment><!--[ Replace data:i &lt;= 0 with data:i &lt;= 1 to display two labels ]--></b:comment>
                                    <b:if cond='data:i &lt;= 0'>
                                      <b:tag cond='data:widget.type != &quot;PopularPosts&quot;' name='span'>
                                        <b:tag expr:data-text='data:label.name' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;span&quot;'>
                                          <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                                          <b:attr cond='data:blog.url != data:label.url' name='rel' value='tag'/>
                                          <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                                        </b:tag>
                                      </b:tag>
                                    </b:if>
                
                                  </b:if>
                                </b:loop>
                              </b:if>
                            </div>
                          </b:if>
                        </b:includable>
                        <b:includable id='postLocation'/>
                        <b:includable id='postMeta' var='post'>
                          <b:include data='post' name='postMetadataJSON'/>
                        </b:includable>
                        <b:includable id='postMetadataJSON'>
                          <script type='application/ld+json'>
                            {
                              &quot;@context&quot;: &quot;http://schema.org&quot;,
                              &quot;@type&quot;: &quot;BlogPosting&quot;,
                              &quot;mainEntityOfPage&quot;: {
                                &quot;@type&quot;: &quot;WebPage&quot;,
                                &quot;@id&quot;: &quot;<data:post.url.canonical.jsonEscaped/>&quot;
                              },
                              &quot;headline&quot;: &quot;<data:post.title.jsonEscaped/>&quot;,
                              &quot;description&quot;: &quot;<b:eval expr='snippet(data:post.snippets.long, {length: 250, links: false, linebreaks: false, ellipsis: true }).jsonEscaped'/>&quot;,
                              <b:if cond='data:view.isSingleItem'>&quot;articleBody&quot;: &quot;<b:eval expr='snippet(data:post.body, {links: false, linebreaks: false, ellipsis: true}).jsonEscaped'/>&quot;,</b:if>
                              &quot;datePublished&quot;: &quot;<data:post.date.iso8601.jsonEscaped/>&quot;,
                              &quot;dateModified&quot;: &quot;<data:post.lastUpdated.iso8601.jsonEscaped/>&quot;,
                              <b:include data='post' name='postMetadataJSONImage'/><b:include data='post' name='postMetadataJSONPublisher'/>
                              &quot;author&quot;: {
                                &quot;@type&quot;: &quot;Person&quot;,
                                &quot;name&quot;: &quot;<data:post.author.name.jsonEscaped/>&quot;,
          
                                /* Get Blogger profile url, otherwise homepage url will be shown */
                                &quot;url&quot;: &quot;<b:if cond='data:post.author.profileUrl'><data:post.author.profileUrl.jsonEscaped/><b:else/><data:blog.homepageUrl.jsonEscaped/></b:if>&quot;,
          
                                /* Get Blogger profile photo, otherwise Blogger logo will be shown */
                                &quot;image&quot;: &quot;<b:if cond='data:post.author.authorPhoto.image'><data:post.author.authorPhoto.image.jsonEscaped/><b:else/>https://www.blogger.com/img/blogger_logo_round_35.png</b:if>&quot;
                              }
                            }
                          </script>
                        </b:includable>
                        <b:includable id='postMetadataJSONImage'>
                          &quot;image&quot;: {
                            &quot;@type&quot;: &quot;ImageObject&quot;,
        
                            /* Get the first image, otherwise no default image will be shown */
                            &quot;url&quot;: &quot;<b:eval expr='(data:post.featuredImage ? resizeImage(data:post.featuredImage, 1200, &quot;1200:630&quot;) : &quot;https://1.bp.blogspot.com/-E250bQMM8tk/XomH5DdorOI/AAAAAAAAPY8/SCYwi79WjckWC8wHKK7OblI82BpT9JquACNcBGAsYHQ/s1600/jagotheme-img.png&quot;)'/>&quot;,
                            &quot;height&quot;: <b:eval expr='data:post.featuredImage ? 630 : 420'/>,
                            &quot;width&quot;: 1200
                          },
                        </b:includable>
                        <b:includable id='postMetadataJSONPublisher'>
                          &quot;publisher&quot;: {
                            &quot;@type&quot;: &quot;Organization&quot;,
                            &quot;name&quot;: &quot;<data:blog.title.escaped/>&quot;,
                            &quot;logo&quot;: {
                              &quot;@type&quot;: &quot;ImageObject&quot;,
                              &quot;url&quot;: &quot;https://1.bp.blogspot.com/-50s1RMWV7jI/X8OaYjJcMiI/AAAAAAAAQK4/sWcpbaP0Sq0hsW473Vnb8AyBvYvdSQEPwCNcBGAsYHQ/s0/jd-logo.png&quot;,
                              &quot;width&quot;: 297,
                              &quot;height&quot;: 45
                            }
                          },
                        </b:includable>
                        <b:includable id='postReactions'/>
                        <b:includable id='postShareButtons'/>
                        <b:includable id='postSnippet'>
                          <div class='pS fontM'>
                            <b:class cond='!data:post.featuredImage' name='noImage'/>
                            <b:class cond='data:post.title.length lt 25' name='show'/>
          
                            <div class='snippet clamp'>
                              <b:class cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])' name='opacity'/>
                              <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='prices'/>
            
                              <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                <b:eval expr='snippet(data:post.snippets.long, {length: 150, links: false, linebreaks: false})'/>
            
                                <b:else/>
                                <b:comment>Use this to hide image captions in article snippets</b:comment>
                                <b:eval expr='snippet(data:post.body, {length: 150, links: false, linebreaks: false})'/>
                              </b:if>
                            </div>
                          </div>
                        </b:includable>
                        <b:includable id='postTimestamp'/>
                        <b:includable id='postTitle' var='post'>
                          <b:if cond='data:post.title != &quot;&quot;'>
                            <div class='pT cInherit'>
                              <b:tag class='name' expr:name='data:post.link or (data:post.url and data:view.url != data:post.url) ? &quot;h2&quot; : &quot;h1&quot;'>
                                <b:class cond='data:view.isSingleItem' name='item'/>
                                <b:attr cond='data:view.isSingleItem and data:widget.type == &quot;Blog&quot;' name='id' value='postT'/>

                                <b:if cond='data:post.link or (data:post.url and data:view.url != data:post.url)'>
                                  <a class='clamp' expr:href='data:post.link ?: data:post.url'><data:post.title/></a>
                                  <b:else/>
                                  <data:post.title/>
                                </b:if>
                              </b:tag>
                            </div>
                          </b:if>
                        </b:includable>
                        <b:includable id='sharingButton'/>
                        <b:includable id='sharingButtonContent'/>
                        <b:includable id='sharingButtons'/>
                        <b:includable id='sharingButtonsMenu'/>
                        <b:includable id='sharingPlatformIcon'/>
                        <b:includable id='snippetedPostByline'/>
                        <b:includable id='snippetedPostContent'>
                          <!--[ Post thumbnails ]-->
                          <b:include cond='data:this.postDisplay.showFeaturedImage and data:post.featuredImage' name='snippetedPostThumbnail'/>
                          
                          <!--[ Post content (title, body, etc.) ]-->
                          <b:tag class='pC grow' name='div'>
                            <b:class name='flex column'/>
                            
                            <b:include name='postInfo'/>
                            <b:include cond='data:this.postDisplay.showTitle' name='snippetedPostTitle'/>
                            <b:include cond='data:this.postDisplay.showSnippet' data='post' name='postSnippet'/>
                            
                            <!--[ Post footer ]-->
                            <b:include cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])' data='post' name='postFooter'/>
                            
                            <!--[ Meta rich results ]-->
                            <b:include data='post' name='postMeta'/>
                          </b:tag>
                        </b:includable>
                        <b:includable id='snippetedPostThumbnail'>
                          <div class='pI cInherit'>
                            <b:class cond='(data:view.isMultipleItems and data:widget.type == &quot;Blog&quot;) or data:widget.type == &quot;FeaturedPost&quot; or data:widget.type == &quot;PopularPosts&quot;' name='shrink'/>
                            <b:class cond='data:post.featuredImage.isYoutube' name='youtube'/>
                            <b:class cond='!data:post.featuredImage' name='noImage'/>

                            <b:tag class='thumbnail' expr:name='data:post.featuredImage ? &quot;a&quot; : &quot;div&quot;'>
                              <b:attr cond='data:post.featuredImage' expr:value='data:post.url' name='href'/>
                              <b:if cond='data:post.featuredImage'>
                                <b:include name='postThumbnail'/>
                                <b:else/>
                                <b:comment>If there is no thumbnail, an empty block will be displayed</b:comment>
                                <span class='img null noWrap opacity'/>
                              </b:if>
                            </b:tag>
                            
                            <div class='bar flexIn'>
                              <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
          
                              <b:if cond='data:widget.type != &quot;PopularPosts&quot;'>
                                <b:comment>Add to bookmark</b:comment>
                                <div class='ignielBookmarkPost tag addl'>
                                  <input class='hidden addb' expr:id='&quot;bm-&quot; + data:post.id' name='bookmark' type='checkbox'/>
                                  <label aria-label='Add bookmark' class='flex center op i16' expr:data-img='data:post.featuredImage ? resizeImage(data:post.featuredImage, 80, &quot;1:1&quot;) :  &quot;data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=&quot;' expr:data-title='data:post.title' expr:data-url='data:post.url' expr:for='&quot;bm-&quot; + data:post.id' title='Add to bookmark'>
                                    <b:include name='archive-add-icon'/>
                                    <b:include name='archive-tick-icon'/>
                                  </label>
                                </div>
                              </b:if>
            
                              <b:comment>Comment count</b:comment>
                              <b:if cond='(data:post.allowComments and data:post.numberOfComments &gt; 0) and data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                <b:if cond='data:widgets.Blog.first.allBylineItems.comments'>
                                  <b:include name='commentCount'/>
                                </b:if>
                              </b:if>
          
                              <b:comment>Product icon</b:comment>
                              <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                <b:class name='product'/>
                                <span class='flex center op i16 tag'><b:include name='tag-icon'/></span>
              
                                <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                                  <span class='flex center discount'>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount10&quot; ])' name='data-text' value='-10%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount20&quot; ])' name='data-text' value='-20%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount30&quot; ])' name='data-text' value='-30%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount40&quot; ])' name='data-text' value='-40%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount50&quot; ])' name='data-text' value='-50%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount60&quot; ])' name='data-text' value='-60%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount70&quot; ])' name='data-text' value='-70%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount80&quot; ])' name='data-text' value='-80%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount90&quot; ])' name='data-text' value='-90%'/>
                                  </span>
                                </b:if>
                              </b:if>
                            </div>
                            
                          </div>
                        </b:includable>
                        <b:includable id='snippetedPostTitle'>
                          <!--[ Post title ]-->
                          <b:include data='post' name='postTitle'/>
                        </b:includable>
                        <b:includable id='snippetedPosts'>
                          <div class='itemP featured' role='feed'>
                            <!-- Don't render the post that we're currently already looking at. -->
                            <b:loop values='data:posts filter (p =&gt; p.id != data:view.postId)' var='post'>
                              <article class='i flex wrap'>
                                <b:class cond='data:view.isMultipleItems and !data:post.featuredImage' name='noImage'/>
                                <b:class cond='!data:widgets.Blog.first.allBylineItems.timestamp' name='noTime'/>
                                <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
                                <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='shop'/>
                                
                                <b:include name='snippetedPostContent'/>
                              </article>
                            </b:loop>
                          </div>
                        </b:includable>
                      </b:widget>
                    </b:section>
                    
                    <b:section class='flex column' id='main-widget' showaddelement='true'>
                      <b:widget cond='(!data:view.isPreview and !data:blog.isMobileRequest) and data:view.isHomepage' id='HTML93' locked='true' title='Ads go here' type='HTML' version='2' visible='false'>
                        <b:widget-settings>
                          <b:widget-setting name='content'/>
                        </b:widget-settings>
                        <b:includable id='main'>
                          <b:if cond='data:content != &quot;&quot;'>
                            <data:content/>
                        
                            <b:else/>
                            <!--[ Blank ad ]-->
                            <div class='adB' expr:data-text='data:messages.adsGoHere'/>
                          </b:if>
                        </b:includable>
                      </b:widget>
                      <b:widget id='Blog1' locked='true' title='رسائل المدونة الإلكترونية' type='Blog' version='2' visible='true'>
                        <b:widget-settings>
                          <b:widget-setting name='showDateHeader'>false</b:widget-setting>
                          <b:widget-setting name='commentLabel'>Comment</b:widget-setting>
                          <b:widget-setting name='style.textcolor'>#ffffff</b:widget-setting>
                          <b:widget-setting name='showShareButtons'>true</b:widget-setting>
                          <b:widget-setting name='authorLabel'>Oleh</b:widget-setting>
                          <b:widget-setting name='showCommentLink'>true</b:widget-setting>
                          <b:widget-setting name='style.urlcolor'>#ffffff</b:widget-setting>
                          <b:widget-setting name='showAuthor'>true</b:widget-setting>
                          <b:widget-setting name='style.linkcolor'>#ffffff</b:widget-setting>
                          <b:widget-setting name='style.unittype'>TextAndImage</b:widget-setting>
                          <b:widget-setting name='style.bgcolor'>#ffffff</b:widget-setting>
                          <b:widget-setting name='timestampLabel'>Update and timeAgo</b:widget-setting>
                          <b:widget-setting name='reactionsLabel'/>
                          <b:widget-setting name='showAuthorProfile'>true</b:widget-setting>
                          <b:widget-setting name='style.layout'>1x1</b:widget-setting>
                          <b:widget-setting name='showLabels'>true</b:widget-setting>
                          <b:widget-setting name='showLocation'>false</b:widget-setting>
                          <b:widget-setting name='postLabelsLabel'>in</b:widget-setting>
                          <b:widget-setting name='showTimestamp'>true</b:widget-setting>
                          <b:widget-setting name='postsPerAd'>1</b:widget-setting>
                          <b:widget-setting name='showBacklinks'>false</b:widget-setting>
                          <b:widget-setting name='style.bordercolor'>#ffffff</b:widget-setting>
                          <b:widget-setting name='showInlineAds'>false</b:widget-setting>
                          <b:widget-setting name='showReactions'>false</b:widget-setting>
                        </b:widget-settings>
                        <b:includable id='main' var='this'>
                      
                          <b:comment>Showing title and breadcrumbs</b:comment>
                          <b:include name='titleAndBreadcrumbs'/>
                  
                          <b:tag class='blogP' name='div'>
                            <b:class cond='data:view.isMultipleItems' name='flex wrap'/>
                            <b:class cond='data:posts.empty' name='n'/>
                        
                            <b:comment>If the post has a label: Product</b:comment>
                            <b:if cond='data:view.isMultipleItems and data:view.search.label == &quot;Product&quot;'>
                              <b:class name='product'/>
                            </b:if>
                        
                            <b:comment>If the post has a label: Fullpage</b:comment>
                            <b:if cond='data:view.isSingleItem and data:posts any (p =&gt; p.labels any (l =&gt; l.name in [ &quot;Fullpage&quot; ]))'>
                              <b:class name='full'/>
                              <b:include name='postFullpage'/>
                            </b:if>
                        
                            <b:comment>If no content was found</b:comment>
                            <b:include name='noContentPlaceholder'/>

                            <b:comment>Cap the total number of ads (widgets and inline rds).</b:comment>
                            <b:with value='3' var='maxNumAds'>
                              <b:with value='data:widgets.AdSense.size' var='numDesktopAds'>
                                <b:with value='data:widgets.AdSense count (w =&gt; w.sectionId != &quot;ads&quot;)' var='numMobileAds'>
                             
                                  <b:comment>Filter out the featured post, but only on the homepage.</b:comment>
                                  <b:with value='data:widgets.FeaturedPost filter (w =&gt; w.sectionId == &quot;top-widget&quot;) map (w =&gt; w.postId)' var='featuredPostIds'>
                                    <b:with value='data:view.isHomepage ? data:posts filter (post =&gt; post.id not in data:featuredPostIds) : data:posts' var='posts'>
                                      
                                        <b:loop index='i' values='data:posts' var='post'>
                              
                                          <b:comment>Remove comment tag below to enable in-feed ad</b:comment>
                                          <!--<b:if cond='data:i == 2'>
                                            <b:include name='post-adI'/>
                                          </b:if>
                                          <b:if cond='data:i == 6'>
                                            <b:include name='post-adI'/>
                                          </b:if>-->
                                        
                                          <b:include data='post' name='postCommentsAndAd'/>
                                        </b:loop>
                                      
                                    </b:with>
                                  </b:with>
                             
                                </b:with>
                              </b:with>
                            </b:with>
                        
                          </b:tag>
                    
                          <b:comment>Post navigation is hidden when no content found</b:comment>
                          <b:include cond='data:olderPageUrl and data:view.isMultipleItems and !data:posts.empty' name='postPagination'/>
                    
                          <b:comment>timeAgo script</b:comment>
                          <b:loop index='b' values='data:posts' var='post'>
                            <b:if cond='data:b == 0'>
                              <b:if cond='(data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;timeAgo&quot; or data:widgets.Blog.first.allBylineItems.timestamp.label == &quot;Update and timeAgo&quot;) or (data:post.allowComments and data:post.numberOfComments &gt; 0)'>
                                <script>/*<![CDATA[*/ /* Javascript TimeAgo, source: coderwall.com/p/uub3pw/javascript-timeago-func-e-g-8-hours-ago */ (function timeAgo(selector) { var templates = {prefix: "", suffix: " ago", seconds: "few seconds", minute: "a minute", minutes: "%d minutes", hour: "an hour", hours: "%d hours", day: "a day", days: "%d days", month: "a month", months: "%d months", year: "a year", years: "%d years" }; var template = function (t, n) { return templates[t] && templates[t].replace(/%d/i, Math.abs(Math.round(n))); }; var timer = function (time) { if (!time) return; time = time.replace(/\.\d+/, ""); time = time.replace(/-/, "/").replace(/-/, "/"); time = time.replace(/T/, " ").replace(/Z/, " UTC"); time = time.replace(/([\+\-]\d\d)\:?(\d\d)/, " $1$2"); time = new Date(time * 1000 || time); var now = new Date(); var seconds = ((now.getTime() - time) * .001) >> 0; var minutes = seconds / 60; var hours = minutes / 60; var days = hours / 24; var years = days / 365; return templates.prefix + (seconds < 45 && template("seconds", seconds) || seconds < 90 && template("minute", 1) || minutes < 45 && template("minutes", minutes) || minutes < 90 && template("hour", 1) || hours < 24 && template("hours", hours) || hours < 42 && template("day", 1) || days < 30 && template("days", days) || days < 45 && template("month", 1) || days < 365 && template("months", days / 30) || years < 1.5 && template("year", 1) || template("years", years)) + templates.suffix; }; var elements = document.getElementsByClassName("timeAgo"); for (var i in elements) { var $this = elements[i]; if (typeof $this === "object") { $this.innerHTML = timer($this.getAttribute("datetime") || $this.getAttribute("data-time")); }; }; setTimeout(timeAgo, 1000); })(); /*]]>*/</script>
                              </b:if>
                            </b:if>
                          </b:loop>
                            
                        </b:includable>
                        <b:includable id='aboutPostAuthor'>
                          <div class='authors flex fontM'>
                            <div class='img shrink'>
                              <b:include name='postAuthorImage'/>
                            </div>
                            <div class='name'>
                              <b:tag class='namei hidden' cond='data:post.author.aboutMe.length &gt; 200' id='forAuthor' name='input' type='checkbox'/>
            
                              <bdi class='m cInherit' expr:data-text='data:post.author.name' expr:data-write='data:messages.postedBy'/>
                              <div class='d flex'>
                                <div class='clamp'><b:eval expr='data:post.author.aboutMe snippet {links: true, linebreaks: true}'/></div>
                                <b:tag aria-label='Show description' class='shrink' expr:data-text='data:messages.showAll' for='forAuthor' name='label'/>
                              </div>
            
                            </div>
                          </div>
                        </b:includable>
                        <b:includable id='addComments'>
                          <div class='cmD cmButton'>
                            <a class='cmW button' expr:href='data:post.commentsUrl' rel='noreferrer' role='button' target='_blank'>
                              <b:attr cond='data:post.commentsUrlOnclick' expr:value='data:post.commentsUrlOnclick' name='onclick'/>
                              <!--[ Delete tag below to change button style ]-->
                              <b:class name='ln'/>
                              <b:message name='messages.postAComment'/>
                            </a>
                          </div>
                        </b:includable>
                        <b:includable id='blogThisShare'>
                          <b:with value='&quot;window.open(this.href, \&quot;_blank\&quot;, \&quot;height=270,width=475\&quot;); return false;&quot;' var='onclick'>
                            <b:include name='platformShare'/>
                          </b:with>
                        </b:includable>
                        <b:includable id='bylineByName' var='byline'/>
                        <b:includable id='bylineRegion' var='regionItems'/>
                        <b:includable id='commentAuthorAvatar'>
                          <div class='cmA shrink'>
                            <b:class cond='data:comment.level.author == data:post.author.name' name='admin'/>
                            <b:if cond='data:comment.level.authorAvatarSrc'>
                              <div class='avatar im flex center bgAlt' expr:data-style='&quot;background-image: url(&quot; + resizeImage(data:comment.level.authorAvatarSrc, 35, &quot;1:1&quot;) + &quot;)&quot;'>
                                <b:class cond='!data:view.isPreview' name='lazy'/>
                                <b:attr cond='data:view.isPreview' expr:value='&quot;background-image: url(&quot; + resizeImage(data:comment.level.authorAvatarSrc, 35, &quot;1:1&quot;) + &quot;)&quot;' name='style'/>
                              </div>
                              <noscript><div class='avatar im flex center bgAlt' expr:style='&quot;background-image: url(&quot; + resizeImage(data:comment.level.authorAvatarSrc, 35, &quot;1:1&quot;) + &quot;)&quot;'/></noscript>
                            </b:if>
                          </div>
                        </b:includable>
                        <b:includable id='commentDeleteIcon' var='comment'><b:comment>Removed</b:comment></b:includable>
                        <b:includable id='commentForm' var='post'>
                          <div id='commentForm'>
                            <!--[ Comment message ]-->
                            <b:if cond='data:this.messages.blogComment != &quot;&quot;'>
                              <div class='cmm note noJava'>
                                <data:this.messages.blogComment/>
                              </div>
                            </b:if>
                        
                            <b:include name='commentIframe'/>
                          </div>
                        </b:includable>
                        <b:includable id='commentFormIframeSrc' var='post'>
                          <a aria-label='Comment Form' expr:href='data:post.commentFormIframeSrc + &quot;&amp;skin=contempo&quot; + data:variantParam' id='comment-editor-src'/>
                        </b:includable>
                        <b:includable id='commentItem' var='comment'>
                          <b:include cond='data:blog.enabledCommentProfileImages' name='commentAuthorAvatar'/>
                        
                          &lt;div class=&#39;cmI&#39;&gt;
                      
                          <div class='cmB comment-block'>
                            <b:class cond='data:comment.level.isDeleted' name='delete'/>
                            <b:attr cond='!data:comment.level.isDeleted' name='itemscope' value='itemscope'/>
                            <b:attr cond='!data:comment.level.isDeleted' name='itemtype' value='https://schema.org/Comment'/>
                        
                            <div class='cmT comment-author flexIn baseline ellips'>
                              <b:class cond='data:comment.level.author == data:post.author.name' name='admin'/>
                              <span class='n'>
                                <b:class cond='data:comment.level.author == data:post.author.name' name='flexIn i16'/>
                                <b:attr cond='!data:comment.level.isDeleted' name='itemprop' value='author'/>
                                <b:attr cond='!data:comment.level.isDeleted' name='itemscope' value='itemscope'/>
                                <b:attr cond='!data:comment.level.isDeleted' name='itemtype' value='https://schema.org/Person'/>
                                <b:if cond='data:comment.level.author != &quot;Anonymous&quot;'>
                                  <bdi><b:attr cond='!data:comment.level.isDeleted' name='itemprop' value='name'/><data:comment.level.author/></bdi>
                                  <b:else/>
                                  <bdi><b:attr cond='!data:comment.level.isDeleted' name='itemprop' value='name'/>Anonymous</bdi>
                                </b:if>
                          
                                <b:if cond='data:comment.level.author == data:post.author.name'>
                                  <b:include name='admin-icon'/>
                                </b:if>
                              </span>
                          
                              <b:if cond='!data:comment.level.isDeleted'>
                                <b:if cond='data:blog.languageDirection != &quot;rtl&quot;'>
                                  <span class='time fontSm opacity' expr:data-time='data:comment.level.timestamp'>
                                    <b:comment><!--[ Remove <b:class name='timeAgo'/> to disable Second Ago script ]--></b:comment>
                                    <b:class name='timeAgo'/>
                                    <data:comment.level.timestamp/>
                                  </span>
                                </b:if>
                                <span class='time fontSm opacity' expr:data-time='data:comment.level.timestamp' itemprop='datePublished'>
                                  <b:class cond='data:blog.languageDirection != &quot;rtl&quot;' name='hidden'/>
                                  <data:comment.level.timestamp/>
                                </span>
                              </b:if>
                            </div>
                        
                            <b:tag expr:class='&quot;cmC comment-body&quot; + (data:comment.level.isDeleted ? &quot; delete ellips opacity fontM&quot; : &quot;&quot;)' expr:name='data:comment.level.isDeleted ? &quot;i&quot; : &quot;div&quot;'>
                              <b:attr cond='!data:comment.level.isDeleted' name='itemprop' value='text'/>
                              <b:if cond='data:comment.level.author != data:post.author.name'>
                                <b:eval expr='data:comment.level.body snippet { links: false }'/>
                                <b:else/>
                                <data:comment.level.body/>
                              </b:if>
                            </b:tag>
                        
                            <b:if cond='!data:comment.level.isDeleted and data:post.allowNewComments'>
                              <div class='cmJ comment-footer cInherit opacity fontM noJava'>
                                <b:with value='data:post.comments where (c =&gt; c.inReplyTo == data:commentLevel1.id)' var='commentL2'>
                                  <b:if cond='data:commentL2.size != &quot;0&quot;'>
                                    <b:comment>Remove below tag to show [Delete comment] button</b:comment>
                                    <b:class name='hidden'/>
                                  </b:if>
                                </b:with>
                          
                                <b:if cond='data:comment.d and data:post.allowNewComments'>
                                  <a aria-label='Reply' class='r rpT' data-text='Relpy' expr:data-reply-to='data:commentLevel1.id' href='javascript:;' target='_self'/>
                                </b:if>
                            
                                <b:comment>Delete comments button</b:comment>
                                <!--<span class='r item-control'>
                                  <b:class expr:name='data:comment.level.adminClass'/>
                                  <a aria-label='Delete' class='d' data-text='Delete' expr:href='data:comment.level.deleteUrl' expr:title='data:messages.deleteComment' rel='noreferrer noopener' target='_blank'/>
                                </span>-->
                              </div>
                            </b:if>
                      
                          </div>
                        </b:includable>
                        <b:includable id='commentList' var='comments'>
                          <ol class='cmO flex column noList' id='comments-block'>
                            <b:class cond='!data:post.allowNewComments' name='n'/>
                            <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                            <b:loop values='data:post.comments where (c =&gt; not c.inReplyTo or c.inReplyTo == 0)' var='commentLevel1'>
                              <li class='c flex' expr:id='&quot;c&quot; + data:commentLevel1.id'>
                                <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                          
                                <b:comment>Comment item: All comment content is here</b:comment>
                                <b:include data='{level: data:commentLevel1,d: true}' name='commentItem'/>
                                        
                                <b:with value='data:post.comments where (c =&gt; c.inReplyTo == data:commentLevel1.id)' var='commentL2'>
                                  <b:if cond='data:commentL2.size != &quot;0&quot;'>
                                            
                                    <details class='cmR comment-replies'>
                                      <summary class='n fontM opacity' data-text='Hide replies' expr:aria-label='&quot;View &quot; +data:commentL2.length+ &quot; replies&quot;'>
                                        <b:if cond='data:commentL2.length == 1'>
                                          <b:attr name='data-text' value='Hide reply'/>
                                          <b:attr expr:value='&quot;View &quot; +data:commentL2.length+ &quot; reply&quot;' name='aria-label'/>
                                        </b:if>
                                      </summary>
                                              
                                      <div class='cmS comment-thread' expr:id='&quot;c-&quot; + data:commentLevel1.id + &quot;-rt&quot;'>
                                        <ol class='noList flex column'>
                                          <b:loop values='data:commentL2' var='commentLevel2'>
                                            <li class='cc' expr:id='&quot;c&quot; + data:commentLevel2.id'>
                                              <b:include data='{level: data:commentLevel2,d: false}' name='commentItem'/>
                                              &lt;/div&gt;
                                            </li>
                                          </b:loop>
                                        </ol>
                                      </div>
                                      <b:if cond='data:post.allowNewComments'>
                                        <div class='cmJ cmc comment-actions noJava'>
                                          <a aria-label='Reply' class='rpT' data-text='Write a reply...' expr:data-reply-to='data:commentLevel1.id' href='javascript:;' target='_self'/>
                                        </div>
                                      </b:if>
                                             
                                    </details>
                                  </b:if>
                                </b:with>
                                        
                                &lt;/div&gt;
                              </li>
                            </b:loop>
                          </ol>
                        </b:includable>
                        <b:includable id='commentPicker' var='post'>
                          <b:comment>Input for comment pop-up</b:comment>
                          <b:tag class='popI hidden' cond='data:post.embedCommentForm or data:post.commentsUrlOnclick' id='forComments' name='input' type='checkbox'/>
                          <b:tag class='cmi hidden' cond='data:post.numberOfComments &gt; 1' id='forAllCm' name='input' type='checkbox'/>
                          
                          <b:comment>Delete tag below to disable show/hide comment</b:comment>
                          <b:if cond='data:post.embedCommentForm or data:post.commentsUrlOnclick'>
                            <b:include cond='data:post.allowComments' name='commentButton'/>
                          </b:if>
                          
                          <b:comment>Modified Blogger comments by jagodesain.com</b:comment>
                          <section expr:class='&quot;cm comments&quot; + (data:post.embedCommentForm ? &quot; embed&quot; : &quot; noEmbed&quot;)' expr:data-num-comments='data:post.numberOfComments' id='comments'>
                            
                            <b:attr cond='data:post.showThreadedComments' expr:value='data:post.embedCommentForm' name='data-embed'/>
                            <b:class cond='!data:post.allowNewComments' name='noNew'/>
                            
                            <b:comment>Delete tag below to disable Pop-up comments</b:comment>
                            <b:class cond='data:post.embedCommentForm or data:post.commentsUrlOnclick' name='popUp'/>
                            
                            <b:if cond='data:post.showThreadedComments'>
                              <b:include data='post' name='threadedComments'/>
                              <b:else/>
                              <b:include data='post' name='comments'/>
                            </b:if>
                            
                          </section>
                      
                          <b:comment>Comment tag script</b:comment>
                          <b:if cond='data:post.numberOfComments &gt; 0'>
                            <script>/*<![CDATA[*/ /* Comment tag, source: dte.web.id/teknis/paket-javascript-fitur-manipulasi */ function repText(id) {var a = document.getElementById(id); if (!a) return; var b = a.innerHTML; b = b.replace(/<i rel="image">(.*?)<\/i>/ig, "<img class='lazy' data-src='$1' src='data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=' alt='Image' \/>"); a.innerHTML = b;} repText("comments-block"); /*]]>*/</script>
                          </b:if>
                        </b:includable>
                        <b:includable id='comments' var='post'>
                          <b:if cond='data:post.allowComments'>
                            <b:tag class='popIn' name='div'>
                              <b:class cond='data:post.numberOfComments == 0' name='n'/>
                              <b:tag class='popC' name='div'>
                           
                                <!--[ Comments header ]-->
                                <div class='cmH popH flex'>
                                  <!--[ Comments title ]-->
                                  <b:tag class='invisible' cond='!data:post.allowNewComments and data:post.embedCommentForm' name='div'>
                                    <b:comment>Hide comment title when new comments are not allowed</b:comment>
                                    <b:include name='commentsTitle'/>
                                  </b:tag>
                            
                                  <b:comment>Sort comments from newest or oldest</b:comment>
                                  <div class='filter flex'>
                                    <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                    <b:if cond='data:post.numberOfComments &gt; 1'>
                                      <label class='s flex center fontS i16' expr:aria-label='data:messages.comments' expr:data-new='data:messages.newest' expr:data-text='data:messages.oldest' for='forAllCm'>
                                        <b:include name='arrow-down-1-icon'/>
                                      </label>
                                    </b:if>
                                    <b:comment>Hide this too if you disable the comment pop-up</b:comment>
                                    <label aria-label='Close' class='c' for='forComments'>
                                      <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                    </label>
                                  </div>
                                </div>
                          
                                <!--[ Comments content ]-->
                                <div class='cmM cmContent'>
                                
                                  <b:if cond='data:post.numberOfComments &gt; 0 and !data:post.embedCommentForm'>
                                    <p class='note wr' style='font-size:small'>You cannot reply to comments if the comment location is not embedded</p>
                                  </b:if>
                        
                                  <div class='cmF comment-footer'>
                                    <b:if cond='data:post.embedCommentForm'>
                                      <b:if cond='data:post.allowNewComments'>
                                        <b:include data='post' name='commentForm'/>
                                        <b:else/>
                                        <b:comment>If comment was disable</b:comment>
                                        <center class='cmd'><data:post.noNewCommentsText/></center>
                                      </b:if>
                                      <b:else/>
                                      <b:if cond='data:post.allowComments'>
                                        <b:include data='post' name='addComments'/>
                                      </b:if>
                                    </b:if>
                                  </div>
                        
                                  <b:tag class='cmN' cond='data:post.numberOfComments &gt; 0' name='div'>
                                    <b:attr expr:value='data:widget.instanceId + &quot;-comments&quot;' name='id'/>
                                    <b:comment>Comment list content</b:comment>
                                    <b:include cond='data:post.comments' data='post.comments' name='commentList'/>
                                  </b:tag>
                              
                                </div>
                              </b:tag>
                            </b:tag>
                          </b:if>
                        
                          <b:tag class='fc' cond='data:post.embedCommentForm or data:post.commentsUrlOnclick' for='forComments' name='label'/>
                        </b:includable>
                        <b:includable id='commentsLink'>
                          <a class='comment-link' expr:href='data:post.commentsUrl' expr:onclick='data:post.commentsUrlOnclick'>
                            <b:include data='{ iconClass: &quot;touch-icon&quot; }' name='commentIcon'/>
                            <span class='num_comments'>
                              <b:if cond='data:post.numberOfComments &gt; 0'>
                                <b:message name='messages.numberOfComments'>
                                  <b:param expr:value='data:post.numberOfComments' name='numComments'/>
                                </b:message>
                                <b:else/>
                                <data:messages.postAComment/>
                              </b:if>
                            </span>
                          </a>
                        </b:includable>
                        <b:includable id='commentsLinkIframe'>
                          <!-- G+ comments, no longer available. The includable is retained for backwards-compatibility. -->
                        </b:includable>
                        <b:includable id='commentsTitle'>
                          <h3 class='title'>
                            <b:if cond='data:post.numberOfComments &gt; 0'>
                              <b:message name='messages.numberOfComments'>
                                <b:param expr:value='data:post.numberOfComments' name='numComments'/>
                              </b:message>
                              <b:else/>
                              <data:messages.joinTheConversation/>
                            </b:if>
                          </h3>
                        </b:includable>
                        <b:includable id='defaultAdUnit'>
                          <b:comment>Clear out style (needs to be a non-empty string)</b:comment>
                          <b:with value='&quot;/* Done in css. */&quot;' var='style'>
                            <b:include name='super.defaultAdUnit'/>
                          </b:with>
                        </b:includable>
                        <b:includable id='emailPostIcon'>
                          <span class='byline post-icons'>
                            <!-- email post links -->
                            <span class='item-action'>
                              <a expr:href='data:post.emailPostUrl' expr:title='data:messages.emailPost'>
                                <b:include data='{ iconClass: &quot;touch-icon sharing-icon&quot; }' name='emailIcon'/>
                              </a>
                            </span>
                          </span>
                        </b:includable>
                        <b:includable id='facebookShare'>
                          <b:with value='&quot;window.open(this.href, \&quot;_blank\&quot;, \&quot;height=430,width=640\&quot;); return false;&quot;' var='onclick'>
                            <b:include name='platformShare'/>
                          </b:with>
                        </b:includable>
                        <b:includable id='feedLinks'><b:comment>Do not show feed links.</b:comment></b:includable>
                        <b:includable id='feedLinksBody' var='links'><b:comment>Removed</b:comment></b:includable>
                        <b:includable id='footerBylines'>
                          <b:if cond='data:widgets.Blog.first.footerBylines'>
                            <b:loop index='i' values='data:widgets.Blog.first.footerBylines' var='region'>
                              <b:if cond='not data:region.items.empty'>
                                <div expr:class='&quot;post-footer-line post-footer-line-&quot; + (data:i + 1)'>
                                  <b:with value='&quot;footer-&quot; + (data:i + 1)' var='regionName'>
                                    <b:include data='region.items' name='bylineRegion'/>
                                  </b:with>
                                </div>
                              </b:if>
                            </b:loop>
                          </b:if>
                        </b:includable>
                        <b:includable id='googlePlusShare'><b:comment>G+ no longer available.</b:comment></b:includable>
                        <b:includable id='headerByline'>
                          <b:include cond='data:view.isMultipleItems or data:widgets.Blog.first.headerByline.items.share' data='{ shareButtonClass: &quot;post-share-buttons-top&quot;, overridden: true }' name='maybeAddShareButtons'/>
                          <b:include name='super.headerByline'/>
                        </b:includable>
                        <b:includable id='homePageLink'><b:comment>Removed</b:comment></b:includable>
                        <b:includable id='iframeComments' var='post'><b:comment>G+ no longer available.</b:comment></b:includable>
                        <b:includable id='inlineAd' var='post'>
                          <div>
                            <b:class cond='data:post.adNumber + data:numDesktopAds lt data:maxNumAds' name='desktop-ad'/>
                            <b:class cond='data:post.adNumber + data:numMobileAds lt data:maxNumAds' name='mobile-ad'/>
                            <b:include data='post' name='super.inlineAd'/>
                          </div>
                        </b:includable>
                        <b:includable id='linkShare'>
                          <b:with value='&quot;window.prompt(\&quot;Copy to clipboard: Ctrl+C, Enter\&quot;, \&quot;&quot; + data:originalUrl + &quot;\&quot;); return false;&quot;' var='onclick'>
                            <b:include name='platformShare'/>
                          </b:with>
                        </b:includable>
                        <b:includable id='nextPageLink'>
                          <b:tag class='np button' expr:data-text='data:messages.older' expr:name='data:olderPageUrl ? &quot;a&quot; : &quot;div&quot;'>
                            <b:class cond='!data:olderPageUrl' name='m'/>
                            <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                        
                            <b:attr cond='data:olderPageUrl' expr:value='data:olderPageUrl' name='href'/>
                            <b:attr cond='data:olderPageUrl' expr:value='data:messages.oldest' name='aria-label'/>
                            <b:if cond='data:blog.languageDirection != &quot;rtl&quot;'>
                              <b:include name='arrow-right-icon'/>
                              <b:else/>
                              <b:include name='arrow-left-icon'/>
                            </b:if>
                          </b:tag>
                        </b:includable>
                        <b:includable id='noContentPlaceholder'>
                          <b:if cond='data:posts.empty'>
                            <b:comment>You can replace <data:messages.noResultsFound/> with <data:messages.theresNothingHere/></b:comment>
                            <div class='n'><data:messages.noResultsFound/>...</div>
                          </b:if>
                        </b:includable>
                        <b:includable id='otherSharingButton'>
                          <span class='sharing-platform-button sharing-element-other' expr:aria-label='data:messages.shareToOtherApps.escaped' expr:data-url='data:originalUrl' expr:title='data:messages.shareToOtherApps.escaped' role='menuitem' tabindex='-1'>
                            <b:with value='{key: &quot;sharingOther&quot;}' var='platform'>
                              <b:include name='sharingPlatformIcon'/>
                            </b:with>
                            <span class='platform-sharing-text'><data:messages.shareOtherApps.escaped/></span>
                          </span>
                        </b:includable>
                        <b:includable id='platformShare'>
                          <a expr:class='&quot;goog-inline-block sharing-&quot; + data:platform.key' expr:data-url='data:originalUrl' expr:href='data:shareUrl + &quot;&amp;target=&quot; + data:platform.target' expr:onclick='data:onclick ? data:onclick : &quot;&quot;' expr:title='data:platform.shareMessage' target='_blank'>
                            <span class='share-button-link-text'>
                              <data:platform.shareMessage/>
                            </span>
                          </a>
                        </b:includable>
                        <b:includable id='post' var='post'>
                          <b:comment>Post info (only appears on multipleItems page)</b:comment>
                          <b:include cond='data:view.isMultipleItems' name='postInfo'/>
                    
                          <!--[ Post title ]-->
                          <b:include data='post' name='postTitle'/>
                      
                          <b:comment>Only displayed on singleItem page</b:comment>
                          <b:if cond='data:view.isSingleItem'>
                            
                            <!--[ Post description ]-->
                            <b:comment>Add a description on the post page only</b:comment>
                            <b:include cond='data:view.isPost' name='postDescription'/>
                      
                            <!--[ Post header ]-->
                            <b:include cond='!data:view.isPage' data='post' name='postHeader'/>
                        
                            <b:comment>Post ad (above article)</b:comment>
                            <!--<b:include cond='data:view.isPost and !data:view.isPreview' name='post-adT'/>-->
                      
                            <!--[ Post body ]-->
                            <b:include data='post' name='postBody'/>
                      
                            <b:comment>Post ad (below article)</b:comment>
                            <!--<b:include cond='data:view.isPost and !data:view.isPreview' name='post-adB'/>-->
                      
                            <b:else/>
                            <b:comment>Show snippet on multipleItems page</b:comment>
                            <b:include data='post' name='postBodySnippet'/>
                          </b:if>
                    
                          <!--[ Post footer ]-->
                          <b:include cond='!data:view.isPage' data='post' name='postFooter'/>
                      
                          <!--[ Meta rich results ]-->
                          <b:include data='post' name='postMeta'/>
                    
                          <b:comment>RedingTime script</b:comment>
                          <b:if cond='data:view.isPost'>
                            <script>/*<![CDATA[*/ function readTime(el) {ret = ""; var length = el.childNodes.length; for(var i = 0; i < length; i++) {var node = el.childNodes[i]; if(node.nodeType != 8) {ret += node.nodeType != 1 ? node.nodeValue : readTime(node);} } return ret;} var words = readTime(document.getElementById("postBody")); var count = words.split(" ").length; var avg = 200; var counted = count / avg; var maincount = Math.round(counted); document.getElementById("timeRead").innerHTML = maincount; /*]]>*/</script>
                          </b:if>
                        </b:includable>
                        <b:includable id='postAuthor'>
                          <span class='byline post-author vcard'>
                            <span class='post-author-label'>
                              <data:byline.label/>
                            </span>
                            <span class='fn'>
                              <b:if cond='data:post.author.profileUrl'>
                                <meta expr:content='data:post.author.profileUrl'/>
                                <a class='g-profile' expr:href='data:post.author.profileUrl' rel='author' title='author profile'>
                                  <span><data:post.author.name/></span>
                                </a>
                                <b:else/>
                                <span><data:post.author.name/></span>
                              </b:if>
                            </span>
                          </span>
                        </b:includable>
                        <b:includable id='postBody' var='post'>
                          <!-- If metaDescription is empty, use the post body as the schema.org description too, for G+/FB snippeting. -->
                          <div expr:class='&quot;pE postBody postID-&quot; + data:post.id' id='postBody'>
                            <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                            <data:post.body/>
                          </div>
                        </b:includable>
                        <b:includable id='postBodySnippet' var='post'>
                          <b:include cond='data:post' data='post' name='postSnippet'/>
                        </b:includable>
                        <b:includable id='postCommentsAndAd' var='post'>
                          <article class='p'>
                            <b:class cond='data:view.isMultipleItems' name='flex column'/>
                            <b:class cond='data:view.isSingleItem' name='post'/>
                            <b:class cond='data:view.isMultipleItems and !data:post.featuredImage' name='noImage'/>
                            <b:class cond='!data:widgets.Blog.first.allBylineItems.timestamp' name='noTime'/>
                            <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
                            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='shop'/>
                        
                            <!--[ Post thumbnails ]-->
                            <b:comment>Replace the [data:view.isMultipleItems] attribute value below with [data:view.isMultipleItems and data:post.featuredImage] to hide the element when there is no thumbnail in the post</b:comment>
                            <b:if cond='data:view.isMultipleItems'>
                              <b:include name='snippetedPostThumbnail'/>
                            </b:if>
                        
                            <!--[ Post content (title, body, etc.) ]-->
                            <b:tag class='pC grow' name='div'>
                              <b:class cond='data:view.isMultipleItems' name='flex column'/>
                              <b:include data='post' name='post'/>
                            </b:tag>
                        
                            <b:comment>replace data:wiew.isPost with data:view.isSingleItem to also display comments on static pages</b:comment>
                            <b:if cond='data:post.allowComments and (!data:view.isPreview and data:view.isPost)'>
                              <b:tag class='pR noPrint' id='comment' name='div'>
                                <!--[ Comments ]-->
                                <b:include data='post' name='commentPicker'/>
                              </b:tag>
                            </b:if>
                        
                            <!--[ Show ad inside post container, after comments, if single item. ]-->
                            <b:include cond='data:view.isSingleItem and data:post.includeAd' data='post' name='inlineAd'/>
                          </article>
                      
                          <!--[ Show ad outside post container (between posts) for feed pages. ]-->
                          <b:include cond='data:view.isMultipleItems and data:post.includeAd' data='post' name='inlineAd'/>
                        </b:includable>
                        <b:includable id='postCommentsLink'>
                          <b:if cond='data:view.isMultipleItems'>
                            <span class='byline post-comment-link container'>
                              <b:include cond='data:post.commentSource != 1' name='commentsLink'/>
                            </span>
                          </b:if>
                        </b:includable>
                        <b:includable id='postDescription'>
                          <b:if cond='data:blog.metaDescription'>
                            <div class='pD opacity'><data:blog.metaDescription/></div>
                          </b:if>
                        </b:includable>
                        <b:includable id='postFooter' var='post'>
                          <b:tag class='pF' name='div'>
                            <b:class cond='data:view.isMultipleItems' name='items flex space-between fontM cInherit'/>
                            <b:class cond='data:view.isSingleItem' name='item flex column'/>
                            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
                            <b:class cond='data:view.isMultipleItems and data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='shop'/>
                            <b:class name='noPrint'/>
                            
                            <b:if cond='data:view.isSingleItem'>
                              <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
                                <b:comment>Show label</b:comment>
                                <b:if cond='data:widgets.Blog.first.allBylineItems.labels and data:post.labels and data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                  <b:include name='postLabel'/>
                                </b:if>
                        
                                <b:comment>Show author profile</b:comment>
                                <b:include cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])' data='post' name='postFooterAuthorProfile'/>
                         
                                <b:comment>Show related post</b:comment>
                                <b:include name='postRelated'/>
                          
                                <b:comment>Show related Ad</b:comment>
                                <!--<b:include name='post-adRelate'/>-->
                              </b:if>
                        
                              <b:comment>Display sharing menu</b:comment>
                              <!--<b:if cond='!data:view.isPreview and (data:post.shareUrl and data:widgets.Blog.first.allBylineItems.share)'>-->
                                <b:include name='postShare'/>
                              <!--</b:if>-->
                            
                              <b:else/>
                              <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                <b:comment>post Footer in MultipleItems page</b:comment>
                                <b:include cond='data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='postTimestamps'/>
                              
                                <b:comment><!--[ Jumplink / read more link ]--></b:comment>
                                <b:include cond='data:blog.jumpLinkMessage != &quot;false&quot;' name='postFooterJumpLink'/>
                              </b:if>
                              
                            </b:if>
                          </b:tag>
                        </b:includable>
                        <b:includable id='postFooterAuthorProfile' var='post'>
                          <b:if cond='data:post.author.aboutMe and data:view.isPost'>
                            <b:include data='post' name='aboutPostAuthor'/>
                          </b:if>
                        </b:includable>
                        <b:includable id='postFooterJumpLink'>
                          <a class='jump jumpLink shrink' expr:aria-label='data:blog.jumpLinkMessage' expr:data-text='data:blog.jumpLinkMessage' expr:href='data:post.url'>
                            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
                          </a>
                        </b:includable>
                        <b:includable id='postHeader' var='post'>
                          <div class='pH flex space-between cInherit fontM noPrint'>
                            <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot;, &quot;Sponsored&quot; ])' name='tag'/>
                            <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                              <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
                                <b:comment>Author photo</b:comment>
                                <b:if cond='data:widgets.Blog.first.allBylineItems.author'>
                                  <b:tag class='byline img flex center shrink' cond='data:post.author.authorPhoto.image' name='div'>
                                    <b:include name='postAuthorImage'/>
                                  </b:tag>
                                </b:if>
                              </b:if>
                              <div class='byline item grow'>
                                <b:if cond='data:widgets.Blog.first.allBylineItems.author and data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
                                  <b:include name='postAuthorName'/>
                                </b:if>
                                  
                                <b:tag class='date' cond='data:widgets.Blog.first.allBylineItems.timestamp' name='span'>
                                  <b:include name='postTimestamps'/>
                              
                                  <b:comment>Estimated/calculated reading time of posts</b:comment>
                                  <b:include name='postTimeread'/>
                                </b:tag>
                              </div>
                            </b:if>
                            
                            <b:comment>Share button and bookmark</b:comment>
                            <div class='byline share flex shrink'>
                              <div class='ignielBookmarkPost'>
                                <input class='hidden addb' expr:id='&quot;bm-&quot; + data:post.id' name='bookmark' type='checkbox'/>
                                <label aria-label='Add bookmark' class='flex center opacity i20' expr:data-img='data:post.featuredImage ? resizeImage(data:post.featuredImage, 100, &quot;1:1&quot;) :  &quot;data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=&quot;' expr:data-title='data:post.title' expr:data-url='data:post.url' expr:for='&quot;bm-&quot; + data:post.id' title='Add to bookmark'>
                                  <b:include name='archive-add-icon'/>
                                  <b:include name='archive-tick-icon'/>
                                </label>
                              </div>
                              
                              <!--<b:if cond='data:post.shareUrl and data:widgets.Blog.first.allBylineItems.share'>-->
                                <b:include name='postShareButton'/>
                              <!--</b:if>-->
                            </div>
                          </div>
                        </b:includable>
                        <b:includable id='postJumpLink'/>
                        <b:includable id='postLabels'>
                          <b:if cond='data:widgets.Blog.first.allBylineItems.labels'>
                            <div class='label ellips cInherit'>
                              <b:attr cond='data:post.labels' expr:value='data:widgets.Blog.first.allBylineItems.labels.label' name='data-text'/>
                              <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='opacity sponsor'/>
                        
                              <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
                                <b:loop values='data:post.labels' var='label'>
                                  <b:if cond='data:label.name == &quot;Sponsored&quot;'>
                                    <b:tag class='extL' expr:data-text='data:label.name' name='span'/>
                                  </b:if>
                                </b:loop>
                                
                                <b:else/>
                                <b:loop values='data:post.labels' var='label'>
                                  <b:if cond='data:label.name == &quot;Product&quot;'>
                                    <b:tag cond='data:widget.type != &quot;PopularPosts&quot;' name='span'>
                                      <b:tag expr:data-text='data:label.name' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;span&quot;'>
                                        <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                                        <b:attr cond='data:blog.url != data:label.url' name='rel' value='tag'/>
                                        <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                                      </b:tag>
                                    </b:tag>
                                  </b:if>
                                </b:loop>
                        
                                <b:loop index='i' values='data:post.labels' var='label'>
                                  <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot;, &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                                  
                                    <b:comment><!--[ Replace data:i &lt;= 0 with data:i &lt;= 0 to display two labels ]--></b:comment>
                                    <b:if cond='data:i &lt;= 0'>
                                      <b:tag cond='data:widget.type != &quot;PopularPosts&quot;' name='span'>
                                        <b:tag expr:data-text='data:label.name' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;span&quot;'>
                                          <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                                          <b:attr cond='data:blog.url != data:label.url' name='rel' value='tag'/>
                                          <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                                        </b:tag>
                                      </b:tag>
                                    </b:if>
                                  
                                  </b:if>
                                </b:loop>
                              </b:if>
                            </div>
                          </b:if>
                        </b:includable>
                        <b:includable id='postLocation'>
                          <span class='byline post-location'>
                            <data:byline.label/>
                            <a expr:href='data:post.location.mapsUrl' target='_blank'><data:post.location.name/></a>
                          </span>
                        </b:includable>
                        <b:includable id='postMeta' var='post'>
                          <b:include data='post' name='postMetadataJSON'/>
                        </b:includable>
                        <b:includable id='postMetadataJSON'>
                          <script type='application/ld+json'>
                            {
                              &quot;@context&quot;: &quot;http://schema.org&quot;,
                              &quot;@type&quot;: &quot;BlogPosting&quot;,
                              &quot;mainEntityOfPage&quot;: {
                                &quot;@type&quot;: &quot;WebPage&quot;,
                                &quot;@id&quot;: &quot;<data:post.url.canonical.jsonEscaped/>&quot;
                              },
                              &quot;headline&quot;: &quot;<data:post.title.jsonEscaped/>&quot;,
                              &quot;description&quot;: &quot;<b:eval expr='snippet(data:post.snippets.long, {length: 250, links: false, linebreaks: false, ellipsis: true }).jsonEscaped'/>&quot;,
                              <b:if cond='data:view.isSingleItem'>&quot;articleBody&quot;: &quot;<b:eval expr='snippet(data:post.body, {links: false, linebreaks: false, ellipsis: true}).jsonEscaped'/>&quot;,</b:if>
                              &quot;datePublished&quot;: &quot;<data:post.date.iso8601.jsonEscaped/>&quot;,
                              &quot;dateModified&quot;: &quot;<data:post.lastUpdated.iso8601.jsonEscaped/>&quot;,
                              <b:include data='post' name='postMetadataJSONImage'/><b:include data='post' name='postMetadataJSONPublisher'/>
                              &quot;author&quot;: {
                                &quot;@type&quot;: &quot;Person&quot;,
                                &quot;name&quot;: &quot;<data:post.author.name.jsonEscaped/>&quot;,
                      
                                /* Get Blogger profile url, otherwise homepage url will be shown */
                                &quot;url&quot;: &quot;<b:if cond='data:post.author.profileUrl'><data:post.author.profileUrl.jsonEscaped/><b:else/><data:blog.homepageUrl.jsonEscaped/></b:if>&quot;,
                        
                                /* Get Blogger profile photo, otherwise Blogger logo will be shown */
                                &quot;image&quot;: &quot;<b:if cond='data:post.author.authorPhoto.image'><data:post.author.authorPhoto.image.jsonEscaped/><b:else/>https://www.blogger.com/img/blogger_logo_round_35.png</b:if>&quot;
                              }
                            }
                          </script>
                        </b:includable>
                        <b:includable id='postMetadataJSONImage'>
                          &quot;image&quot;: {
                            &quot;@type&quot;: &quot;ImageObject&quot;,
                      
                            /* Get the first image, otherwise no default image will be shown */
                            &quot;url&quot;: &quot;<b:eval expr='(data:post.featuredImage ? resizeImage(data:post.featuredImage, 1200, &quot;1200:630&quot;) : &quot;https://1.bp.blogspot.com/-E250bQMM8tk/XomH5DdorOI/AAAAAAAAPY8/SCYwi79WjckWC8wHKK7OblI82BpT9JquACNcBGAsYHQ/s1600/jagotheme-img.png&quot;)'/>&quot;,
                            &quot;height&quot;: <b:eval expr='data:post.featuredImage ? 630 : 420'/>,
                            &quot;width&quot;: 1200
                          },
                        </b:includable>
                        <b:includable id='postMetadataJSONPublisher'>
                          &quot;publisher&quot;: {
                            &quot;@type&quot;: &quot;Organization&quot;,
                            &quot;name&quot;: &quot;<data:blog.title.escaped/>&quot;,
                            &quot;logo&quot;: {
                              &quot;@type&quot;: &quot;ImageObject&quot;,
                              &quot;url&quot;: &quot;https://1.bp.blogspot.com/-50s1RMWV7jI/X8OaYjJcMiI/AAAAAAAAQK4/sWcpbaP0Sq0hsW473Vnb8AyBvYvdSQEPwCNcBGAsYHQ/s0/jd-logo.png&quot;,
                              &quot;width&quot;: 297,
                              &quot;height&quot;: 45
                            }
                          },
                        </b:includable>
                        <b:includable id='postPagination'>
                          <b:tag class='blogN' id='blog-pager' name='div'>
                            <b:class expr:name='data:blog.isMobileRequest ? &quot;fontSm&quot; : &quot;fontM&quot;'/>
                            <b:class cond='!data:olderPageUrl and (data:view.isHomepage or data:view.url == data:blog.homepageUrl.canonical path &quot;search&quot;)' name='n'/>
                      
                            <b:comment>When no content is displayed</b:comment>
                            <!--<b:tag class='button m' cond='!data:olderPageUrl and (data:view.isHomepage or data:view.url == data:blog.homepageUrl.canonical path &quot;search&quot;)' expr:data-text='data:messages.theresNothingHere' name='div'>
                              <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                            </b:tag>-->
                        
                            <b:if cond='!data:posts.empty'>
                              <b:comment>Hide homePageLink button</b:comment>
                              <b:include cond='data:newerPageUrl' name='previousPageLink'/>
                              <b:include cond='data:view.isHomepage or data:view.url != data:blog.homepageUrl.canonical path &quot;search&quot;' name='homePageLink'/>
                              <b:include cond='data:olderPageUrl' name='nextPageLink'/>
                            </b:if>
                          </b:tag>
                        </b:includable>
                        <b:includable id='postReactions'><b:comment>Reaction feature no longer available.</b:comment></b:includable>
                        <b:includable id='postShareButtons' var='post'><b:comment>We call super.postShareButtons from the migrated positions.</b:comment></b:includable>
                        <b:includable id='postSnippet'>
                          <div class='pS fontM'>
                            <b:class cond='!data:post.featuredImage' name='noImage'/>
                            <b:class cond='data:post.title.length lt 25' name='show'/>
          
                            <div class='snippet clamp'>
                              <b:class cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])' name='opacity'/>
                              <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='prices'/>
                              
                              <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                <b:eval expr='snippet(data:post.snippets.long, {length: 150, links: false, linebreaks: false})'/>
                                
                                <b:else/>
                                <b:comment>Use this to hide image captions in article snippets</b:comment>
                                <b:eval expr='snippet(data:post.body, {length: 150, links: false, linebreaks: false})'/>
                              </b:if>
                            </div>
                          </div>
                        </b:includable>
                        <b:includable id='postTimestamp'/>
                        <b:includable id='postTitle' var='post'>
                          <b:if cond='data:post.title != &quot;&quot;'>
                            <div class='pT cInherit'>
                              <b:tag class='name' expr:name='data:post.link or (data:post.url and data:view.url != data:post.url) ? &quot;h2&quot; : &quot;h1&quot;'>
                                <b:class cond='data:view.isSingleItem' name='item'/>
                                <b:attr cond='data:view.isSingleItem and data:widget.type == &quot;Blog&quot;' name='id' value='postT'/>

                                <b:if cond='data:post.link or (data:post.url and data:view.url != data:post.url)'>
                                  <a class='clamp' expr:href='data:post.link ?: data:post.url'><data:post.title/></a>
                                  <b:else/>
                                  <data:post.title/>
                                </b:if>
                              </b:tag>
                            </div>
                          </b:if>
                        </b:includable>
                        <b:includable id='previousPageLink'>
                          <b:tag class='pp button sc' expr:data-text='data:messages.newest' expr:name='data:newerPageUrl ? &quot;a&quot; : &quot;div&quot;'>
                            <b:class cond='!data:newerPageUrl' name='m'/>
                            <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                        
                            <b:attr cond='data:newerPageUrl' expr:value='data:newerPageUrl' name='href'/>
                            <b:attr cond='data:newerPageUrl' expr:value='data:messages.newest' name='aria-label'/>
                            <b:if cond='data:blog.languageDirection != &quot;rtl&quot;'>
                              <b:include name='arrow-left-1-icon'/>
                              <b:else/>
                              <b:include name='arrow-right-1-icon'/>
                            </b:if>
                          </b:tag>
                        </b:includable>
                        <b:includable id='sharingButton'>
                          <span expr:aria-label='data:platform.shareMessage' expr:class='&quot;sharing-platform-button sharing-element-&quot; + data:platform.key' expr:data-href='data:shareUrl + &quot;&amp;target=&quot; + data:platform.target' expr:data-url='data:originalUrl' expr:title='data:platform.shareMessage' role='menuitem' tabindex='-1'>
                            <b:include name='sharingPlatformIcon'/>
                            <span class='platform-sharing-text'><data:platform.name/></span>
                          </span>
                        </b:includable>
                        <b:includable id='sharingButtonContent'>
                          <div class='flat-icon-button ripple'>
                            <b:include name='shareIcon'/>
                          </div>
                        </b:includable>
                        <b:includable id='sharingButtons'>
                          <div class='sharing' expr:aria-owns='&quot;sharing-popup-&quot; + data:sharingId' expr:data-title='data:shareTitle'>
                            <button class='sharing-button touch-icon-button' expr:aria-controls='&quot;sharing-popup-&quot; + data:sharingId' expr:aria-label='data:messages.share.escaped' expr:id='&quot;sharing-button-&quot; + data:sharingId' role='button'>
                              <b:include name='sharingButtonContent'/>
                            </button>
                            <b:include name='sharingButtonsMenu'/>
                          </div>
                        </b:includable>
                        <b:includable id='sharingButtonsMenu'>
                          <div class='share-buttons-container'>
                            <ul aria-hidden='true' class='share-buttons hidden' expr:aria-label='data:messages.share.escaped' expr:id='&quot;sharing-popup-&quot; + data:sharingId' role='menu'>
                              <b:loop values='(data:platforms ?: data:blog.sharing.platforms) filter (p =&gt; p.key not in {&quot;blogThis&quot;})' var='platform'>
                                <li>
                                  <b:include name='sharingButton'/>
                                </li>
                              </b:loop>
                              <li aria-hidden='true' class='hidden'>
                                <b:include name='otherSharingButton'/>
                              </li>
                            </ul>
                          </div>
                        </b:includable>
                        <b:includable id='sharingPlatformIcon'>
                          <b:include data='{ iconClass: (&quot;touch-icon sharing-&quot; + data:platform.key) }' expr:name='data:platform.key + &quot;Icon&quot;'/>
                        </b:includable>
                        <b:includable id='snippetedPostByline'>
                          <b:include name='headerByline'/>
                        </b:includable>
                        <b:includable id='snippetedPostThumbnail'>
                          <div class='pI cInherit'>
                            <b:class cond='(data:view.isMultipleItems and data:widget.type == &quot;Blog&quot;) or data:widget.type == &quot;FeaturedPost&quot; or data:widget.type == &quot;PopularPosts&quot;' name='shrink'/>
                            <b:class cond='data:post.featuredImage.isYoutube' name='youtube'/>
                            <b:class cond='!data:post.featuredImage' name='noImage'/>
        
                            <b:tag class='thumbnail' expr:name='data:post.featuredImage ? &quot;a&quot; : &quot;div&quot;'>
                              <b:attr cond='data:post.featuredImage' expr:value='data:post.url' name='href'/>
                              <b:if cond='data:post.featuredImage'>
                                <b:include name='postThumbnail'/>
                                <b:else/>
                                <b:comment>If there is no thumbnail, an empty block will be displayed</b:comment>
                                <span class='img null noWrap opacity'/>
                              </b:if>
                            </b:tag>
                            
                            <div class='bar flexIn'>
                              <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
          
                              <b:if cond='data:widget.type != &quot;PopularPosts&quot;'>
                                <b:comment>Add to bookmark</b:comment>
                                <div class='ignielBookmarkPost tag addl'>
                                  <input class='hidden addb' expr:id='&quot;bm-&quot; + data:post.id' name='bookmark' type='checkbox'/>
                                  <label aria-label='Add bookmark' class='flex center op i16' expr:data-img='data:post.featuredImage ? resizeImage(data:post.featuredImage, 80, &quot;1:1&quot;) :  &quot;data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=&quot;' expr:data-title='data:post.title' expr:data-url='data:post.url' expr:for='&quot;bm-&quot; + data:post.id' title='Add to bookmark'>
                                    <b:include name='archive-add-icon'/>
                                    <b:include name='archive-tick-icon'/>
                                  </label>
                                </div>
                              </b:if>
            
                              <b:comment>Comment count</b:comment>
                              <b:if cond='(data:post.allowComments and data:post.numberOfComments &gt; 0) and data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                <b:if cond='data:widgets.Blog.first.allBylineItems.comments'>
                                  <b:include name='commentCount'/>
                                </b:if>
                              </b:if>
          
                              <b:comment>Product icon</b:comment>
                              <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                <b:class name='product'/>
                                <span class='flex center op i16 tag'><b:include name='tag-icon'/></span>
              
                                <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                                  <span class='flex center discount'>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount10&quot; ])' name='data-text' value='-10%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount20&quot; ])' name='data-text' value='-20%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount30&quot; ])' name='data-text' value='-30%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount40&quot; ])' name='data-text' value='-40%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount50&quot; ])' name='data-text' value='-50%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount60&quot; ])' name='data-text' value='-60%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount70&quot; ])' name='data-text' value='-70%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount80&quot; ])' name='data-text' value='-80%'/>
                                    <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount90&quot; ])' name='data-text' value='-90%'/>
                                  </span>
                                </b:if>
                              </b:if>
                            </div>
                            
                          </div>
                        </b:includable>
                        <b:includable id='threadedCommentForm' var='post'>
                          <div id='commentForm'>
                            <!--[ Comment message ]-->
                            <b:if cond='data:this.messages.blogComment != &quot;&quot;'>
                              <div class='cmm note noJava'>
                                <data:this.messages.blogComment/>
                              </div>
                            </b:if>
                        
                            <b:include name='commentIframe'/>
                          </div>
                        </b:includable>
                        <b:includable id='threadedCommentJs' var='post'><b:comment>Removed</b:comment></b:includable>
                        <b:includable id='threadedComments' var='post'>
                          <b:tag class='popIn' name='div'>
                            <b:class cond='data:post.numberOfComments == 0' name='n'/>
                            <b:tag class='popC' name='div'>
                            
                              <!--[ Comments header ]-->
                              <div class='cmH popH flex'>
                                <!--[ Comments title ]-->
                                <b:include name='commentsTitle'/>
                            
                                <b:comment>Sort comments from newest or oldest</b:comment>
                                <div class='filter flex'>
                                  <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                  <b:if cond='data:post.numberOfComments &gt; 1'>
                                    <label class='s flex center fontS i16' expr:aria-label='data:messages.comments' expr:data-new='data:messages.newest' expr:data-text='data:messages.oldest' for='forAllCm'>
                                      <b:include name='arrow-down-1-icon'/>
                                    </label>
                                  </b:if>
                                  <b:comment>Hide this too if you disable the comment pop-up</b:comment>
                                  <label aria-label='Close' class='c' for='forComments'>
                                    <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                  </label>
                                </div>
                              </div>
                        
                              <!--[ Comments content ]-->
                              <div class='cmM cmContent'>
                            
                                <div class='cmF comment-footer'>
                                  <b:if cond='data:post.embedCommentForm'>
                                    <b:if cond='data:post.allowNewComments'>
                                      <b:include data='post' name='threadedCommentForm'/>
                                      <b:else/>
                                      <b:comment>If comment was disable</b:comment>
                                      <center class='cmd'><data:post.noNewCommentsText/></center>
                                    </b:if>
                                    <b:else/>
                                    <b:if cond='data:post.allowComments'>
                                      <b:include data='post' name='addComments'/>
                                    </b:if>
                                  </b:if>
                                </div>
                          
                                <b:if cond='data:post.numberOfComments &gt; 0'>
                                  <b:tag class='cmN' name='div'>
                                    <b:attr expr:value='data:widget.instanceId + &quot;-comments&quot;' name='id'/>
                              
                                    <b:if cond='data:post.allowNewComments'>
                                      <div class='hidden' id='cmAd'>
                                        <div aria-label='Berkomentar' class='button ln' role='button'>
                                          <b:message name='messages.postAComment'/>
                                        </div>
                                      </div>
                                    </b:if>
                              
                                    <b:comment>Comment list content</b:comment>
                                    <b:include cond='data:post.comments' data='post.comments' name='commentList'/>
                                  </b:tag>
                            
                                  <script>var comment = true;</script>
                                  <b:else/>
                                  <script>var comment = false;</script>
                                </b:if>
                      
                                <b:if cond='data:showCmtPopup'>
                                  <div id='comment-popup'>
                                    <iframe allowtransparency='allowtransparency' frameborder='0' id='comment-actions' name='comment-actions' scrolling='no'/>
                                  </div>
                                </b:if>
                              </div>
                            </b:tag>
                          </b:tag>
                        
                          <b:tag class='fc' cond='data:post.embedCommentForm or data:post.commentsUrlOnclick' for='forComments' name='label'/>
                      
                          <b:if cond='data:post.allowNewComments'>
                            <script>/*<![CDATA[*/ document.addEventListener("DOMContentLoaded", function() { var a=document, b = a.getElementById("comment-editor"), d = b.getAttribute("data-src"); if (b.setAttribute("src", d), 1 == comment) { var f = a.getElementsByClassName("rpT"), c = a.getElementById("commentForm"), h = f.length, k = function(b, d, e, f) { b.addEventListener("click", function() { var c = b.getAttribute("data-reply-to"); a.getElementById("c" + c).appendChild(d); a.getElementById("commentForm").className = "cmX"; a.getElementById("cmAd").className = "cmD cmButton"; e.src = f + "&parentID=" + c }) }; for (i = 0; i < h; i++) k(f[i], c, b, d); var l = a.getElementsByClassName("cmF")[0]; a.getElementById("cmAd").addEventListener("click", function() { l.appendChild(c); a.getElementById("commentForm").className = "cmX"; a.getElementById("cmAd").className = "cmD hidden"; b.src = d }) } }); /*]]>*/</script>
                          </b:if>
                        </b:includable>
                      </b:widget>
                      <b:widget cond='data:view.isPost and !data:view.isPreview' id='LinkList01' locked='true' title='Middle post Ad 01' type='LinkList' version='2' visible='false'>
                        <b:widget-settings>
                          <b:widget-setting name='sorting'>NONE</b:widget-setting>
                          <b:widget-setting name='text-1'>Code</b:widget-setting>
                          <b:widget-setting name='link-1'>your_ad_code</b:widget-setting>
                          <b:widget-setting name='text-0'>p</b:widget-setting>
                          <b:widget-setting name='link-0'>10</b:widget-setting>
                        </b:widget-settings>
                        <b:includable id='main'>
                          <b:include name='content'/>
                        </b:includable>
                        <b:includable id='content'>
                          <div class='widget-content'>
                            <b:loop index='code' values='data:links' var='link'>
                              <b:if cond='data:link.name == &quot;Code&quot;'>
                                <b:if cond='data:link.target == &quot;your_ad_code&quot;'>
                                  <!--[ Blank ad ]-->
                                  <div class='adB' expr:data-text='data:messages.adsGoHere'/>
                                  <b:else/>
                                  <data:link.target/>
                                </b:if>
                              </b:if>
                            </b:loop>
                          
                            <b:loop index='i' values='data:links' var='link'>
                              <b:if cond='data:i == 0'>
                                <!--[ Script to move widget to the middle of article ]-->
                                <script>function insertAfter(tbh,tgt) {var prt = tgt.parentNode; if (prt.lastChild == tgt) {prt.appendChild(tbh);} else {prt.insertBefore(tbh,tgt.nextSibling);}} var tgt = document.getElementById(&#39;postBody&#39;), midAd01 = document.getElementById(&#39;LinkList01&#39;), showAd01 = tgt.getElementsByTagName(&#39;<data:link.name/>&#39;); if (showAd01.length &gt; 0) {insertAfter(midAd01,showAd01[<data:link.target/>]);};</script>
                              </b:if>
                            </b:loop>
                          </div>
                        </b:includable>
                      </b:widget>
                      <b:widget cond='data:view.isPost and !data:view.isPreview' id='LinkList02' locked='true' title='Middle post Ad 02' type='LinkList' version='2' visible='false'>
                        <b:widget-settings>
                          <b:widget-setting name='sorting'>NONE</b:widget-setting>
                          <b:widget-setting name='text-1'>Code</b:widget-setting>
                          <b:widget-setting name='link-1'>your_ad_code</b:widget-setting>
                          <b:widget-setting name='text-0'>p</b:widget-setting>
                          <b:widget-setting name='link-0'>20</b:widget-setting>
                        </b:widget-settings>
                        <b:includable id='main'>
                          <b:include name='content'/>
                        </b:includable>
                        <b:includable id='content'>
                          <div class='widget-content'>
                            <b:loop index='code' values='data:links' var='link'>
                              <b:if cond='data:link.name == &quot;Code&quot;'>
                                <b:if cond='data:link.target == &quot;your_ad_code&quot;'>
                                  <!--[ Blank ad ]-->
                                  <div class='adB' expr:data-text='data:messages.adsGoHere'/>
                                  <b:else/>
                                  <data:link.target/>
                                </b:if>
                              </b:if>
                            </b:loop>
                          
                            <b:loop index='i' values='data:links' var='link'>
                              <b:if cond='data:i == 0'>
                                <!--[ Script to move widget to the middle of article ]-->
                                <script>function insertAfter(tbh,tgt) {var prt = tgt.parentNode; if (prt.lastChild == tgt) {prt.appendChild(tbh);} else {prt.insertBefore(tbh,tgt.nextSibling);}} var tgt = document.getElementById(&#39;postBody&#39;), midAd02 = document.getElementById(&#39;LinkList02&#39;), showAd02 = tgt.getElementsByTagName(&#39;<data:link.name/>&#39;); if (showAd02.length &gt; 0) {insertAfter(midAd02,showAd02[<data:link.target/>]);};</script>
                              </b:if>
                            </b:loop>
                          </div>
                        </b:includable>
                      </b:widget>
                    </b:section>
                  </main>
                  
                  <b:comment><!--[ Sidebar ]--></b:comment>
                  <b:if cond='!data:view.isPage'>
                    <aside class='sideB flex shrink column noPrint'>
                      <b:section class='flex column' id='side-widget' showaddelement='true'>
                        <b:widget id='PopularPosts00' locked='false' title='Popular Posts' type='PopularPosts' version='2' visible='true'>
                          <b:widget-settings>
                            <b:widget-setting name='numItemsToShow'>5</b:widget-setting>
                            <b:widget-setting name='showThumbnails'>true</b:widget-setting>
                            <b:widget-setting name='showSnippets'>true</b:widget-setting>
                            <b:widget-setting name='timeRange'>ALL_TIME</b:widget-setting>
                          </b:widget-settings>
                          <b:includable id='main' var='this'>
                            <b:include name='widget-title'/>
                            <b:include name='snippetedPosts'/>
                          </b:includable>
                          <b:includable id='blogThisShare'/>
                          <b:includable id='bylineByName' var='byline'/>
                          <b:includable id='bylineRegion' var='regionItems'/>
                          <b:includable id='commentsLink'/>
                          <b:includable id='commentsLinkIframe'/>
                          <b:includable id='emailPostIcon'/>
                          <b:includable id='facebookShare'/>
                          <b:includable id='footerBylines'/>
                          <b:includable id='googlePlusShare'/>
                          <b:includable id='headerByline'/>
                          <b:includable id='linkShare'/>
                          <b:includable id='otherSharingButton'/>
                          <b:includable id='platformShare'/>
                          <b:includable id='postAuthor'/>
                          <b:includable id='postCommentsLink'/>
                          <b:includable id='postHeaders' var='post'>
                            <b:tag class='pH info flex cInherit fontM' name='div'>
                              <b:include cond='data:post.labels none (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='postTimestamps'/>
                              
                              <b:comment>Show label or Sponsored</b:comment>
                              <b:include cond='data:post.labels' name='postLabels'/>
                            </b:tag>
                          </b:includable>
                          <b:includable id='postJumpLink' var='post'/>
                          <b:includable id='postLabels'>
                            <b:if cond='data:widgets.Blog.first.allBylineItems.labels'>
                              <div class='label ellips cInherit'>
                                <b:attr cond='data:post.labels' expr:value='data:widgets.Blog.first.allBylineItems.labels.label' name='data-text'/>
                                <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='opacity sponsor'/>
      
                                <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])'>
                                  <b:loop values='data:post.labels' var='label'>
                                    <b:if cond='data:label.name == &quot;Sponsored&quot;'>
                                      <b:tag class='extL' expr:data-text='data:label.name' name='span'/>
                                    </b:if>
                                  </b:loop>
              
                                  <b:else/>
                                  <b:loop values='data:post.labels' var='label'>
                                    <b:if cond='data:label.name == &quot;Product&quot;'>
                                      <b:tag cond='data:widget.type != &quot;PopularPosts&quot;' name='span'>
                                        <b:tag expr:data-text='data:label.name' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;span&quot;'>
                                          <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                                          <b:attr cond='data:blog.url != data:label.url' name='rel' value='tag'/>
                                          <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                                        </b:tag>
                                      </b:tag>
                                    </b:if>
                                  </b:loop>
      
                                  <b:loop index='i' values='data:post.labels' var='label'>
                                    <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot;, &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                
                                      <b:comment><!--[ Replace data:i &lt;= 0 with data:i &lt;= 0 to display two labels ]--></b:comment>
                                      <b:if cond='data:i &lt;= 0'>
                                        <b:tag cond='data:widget.type != &quot;PopularPosts&quot;' name='span'>
                                          <b:tag expr:data-text='data:label.name' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;span&quot;'>
                                            <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                                            <b:attr cond='data:blog.url != data:label.url' name='rel' value='tag'/>
                                            <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                                          </b:tag>
                                        </b:tag>
                                      </b:if>
                
                                    </b:if>
                                  </b:loop>
                                </b:if>
                              </div>
                            </b:if>
                           </b:includable>
                          <b:includable id='postLocation'/>
                          <b:includable id='postReactions'/>
                          <b:includable id='postShareButtons'/>
                          <b:includable id='postSnippet'>
                            <div class='pS fontM'>
                              <b:class cond='!data:post.featuredImage' name='noImage'/>
                              <b:class cond='data:post.title.length lt 25' name='show'/>
          
                              <div class='snippet clamp'>
                                <b:class cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])' name='opacity'/>
                                <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='prices'/>
            
                                <b:if cond='data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                  <b:eval expr='snippet(data:post.snippets.long, {length: 150, links: false, linebreaks: false})'/>
            
                                  <b:else/>
                                  <b:comment>Use this to hide image captions in article snippets</b:comment>
                                  <b:eval expr='snippet(data:post.body, {length: 150, links: false, linebreaks: false})'/>
                                </b:if>
                              </div>
                            </div>
                          </b:includable>
                          <b:includable id='postTimestamp'/>
                          <b:includable id='postTitle' var='post'>
                            <b:if cond='data:post.title != &quot;&quot;'>
                              <div class='pT cInherit'>
                                <b:tag class='name' expr:name='data:post.link or (data:post.url and data:view.url != data:post.url) ? &quot;h2&quot; : &quot;h1&quot;'>
                                  <b:class cond='data:view.isSingleItem' name='item'/>
                                  <b:attr cond='data:view.isSingleItem and data:widget.type == &quot;Blog&quot;' name='id' value='postT'/>

                                  <b:if cond='data:post.link or (data:post.url and data:view.url != data:post.url)'>
                                    <a class='clamp' expr:href='data:post.link ?: data:post.url'><data:post.title/></a>
                                    <b:else/>
                                    <data:post.title/>
                                  </b:if>
                                </b:tag>
                              </div>
                            </b:if>
                          </b:includable>
                          <b:includable id='sharingButton'/>
                          <b:includable id='sharingButtonContent'/>
                          <b:includable id='sharingButtons'/>
                          <b:includable id='sharingButtonsMenu'/>
                          <b:includable id='sharingPlatformIcon'/>
                          <b:includable id='snippetedPostByline'/>
                          <b:includable id='snippetedPostContent'>
                            <!--[ Post thumbnails ]-->
                            <b:include cond='data:i == 0 and (data:this.postDisplay.showFeaturedImage and data:post.featuredImage)' name='snippetedPostThumbnail'/>
                            
                            <div class='pC flex'>
                              <div class='pB'>
                                <!--[ Post header ]-->
                                <b:include data='post' name='postHeaders'/>
                                
                                <b:include cond='data:this.postDisplay.showTitle' name='snippetedPostTitle'/>
                                <b:include cond='data:this.postDisplay.showSnippet and data:i == 0' data='post' name='postSnippet'/>
                              </div>
                            </div>
                          </b:includable>
                          <b:includable id='snippetedPostThumbnail'>
                            <div class='pI cInherit'>
                              <b:class cond='(data:view.isMultipleItems and data:widget.type == &quot;Blog&quot;) or data:widget.type == &quot;FeaturedPost&quot; or data:widget.type == &quot;PopularPosts&quot;' name='shrink'/>
                              <b:class cond='data:post.featuredImage.isYoutube' name='youtube'/>
                              <b:class cond='!data:post.featuredImage' name='noImage'/>

                              <b:tag class='thumbnail' expr:name='data:post.featuredImage ? &quot;a&quot; : &quot;div&quot;'>
                                <b:attr cond='data:post.featuredImage' expr:value='data:post.url' name='href'/>
                                <b:if cond='data:post.featuredImage'>
                                  <b:include name='postThumbnail'/>
                                  <b:else/>
                                  <b:comment>If there is no thumbnail, an empty block will be displayed</b:comment>
                                  <span class='img null noWrap opacity'/>
                                </b:if>
                              </b:tag>
                            
                              <div class='bar flexIn'>
                                <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
          
                                <b:if cond='data:widget.type != &quot;PopularPosts&quot;'>
                                  <b:comment>Add to bookmark</b:comment>
                                  <div class='ignielBookmarkPost tag addl'>
                                    <input class='hidden addb' expr:id='&quot;bm-&quot; + data:post.id' name='bookmark' type='checkbox'/>
                                    <label aria-label='Add bookmark' class='flex center op i16' expr:data-img='data:post.featuredImage ? resizeImage(data:post.featuredImage, 80, &quot;1:1&quot;) :  &quot;data:image/png;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=&quot;' expr:data-title='data:post.title' expr:data-url='data:post.url' expr:for='&quot;bm-&quot; + data:post.id' title='Add to bookmark'>
                                      <b:include name='archive-add-icon'/>
                                      <b:include name='archive-tick-icon'/>
                                    </label>
                                  </div>
                                </b:if>
            
                                <b:comment>Comment count</b:comment>
                                <b:if cond='(data:post.allowComments and data:post.numberOfComments &gt; 0) and data:post.labels none (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                  <b:if cond='data:widgets.Blog.first.allBylineItems.comments'>
                                    <b:include name='commentCount'/>
                                  </b:if>
                                </b:if>
          
                                <b:comment>Product icon</b:comment>
                                <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])'>
                                  <b:class name='product'/>
                                  <span class='flex center op i16 tag'><b:include name='tag-icon'/></span>
              
                                  <b:if cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount10&quot;, &quot;Discount20&quot;, &quot;Discount30&quot;, &quot;Discount40&quot;, &quot;Discount50&quot;, &quot;Discount60&quot;, &quot;Discount70&quot;, &quot;Discount80&quot;, &quot;Discount90&quot; ])'>
                                    <span class='flex center discount'>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount10&quot; ])' name='data-text' value='-10%'/>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount20&quot; ])' name='data-text' value='-20%'/>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount30&quot; ])' name='data-text' value='-30%'/>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount40&quot; ])' name='data-text' value='-40%'/>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount50&quot; ])' name='data-text' value='-50%'/>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount60&quot; ])' name='data-text' value='-60%'/>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount70&quot; ])' name='data-text' value='-70%'/>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount80&quot; ])' name='data-text' value='-80%'/>
                                      <b:attr cond='data:post.labels any (label =&gt; label.name in [ &quot;Discount90&quot; ])' name='data-text' value='-90%'/>
                                    </span>
                                  </b:if>
                                </b:if>
                              </div>
                              
                            </div>
                          </b:includable>
                          <b:includable id='snippetedPostTitle'>
                            <!--[ Post title ]-->
                            <b:include data='post' name='postTitle'/>
                          </b:includable>
                          <b:includable id='snippetedPosts'>
                            <div class='itemP popular flex column' role='feed'>
                              <!-- Don't render the post that we're currently already looking at. -->
                              <b:loop index='i' values='data:posts filter (p =&gt; p.id != data:view.postId)' var='post'>
                                <article class='i'>
                                  <b:class cond='data:i == 0 and (data:this.postDisplay.showFeaturedImage and !data:post.featuredImage)' name='noImage'/>
                                  <b:class cond='data:i == 0 and (data:this.postDisplay.showFeaturedImage and data:post.featuredImage)' name='most flex column'/>
                                  <b:class cond='!data:widgets.Blog.first.allBylineItems.timestamp' name='noTime'/>
                                  <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                  <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Sponsored&quot; ])' name='sponsor'/>
                                  <b:class cond='data:post.labels any (label =&gt; label.name in [ &quot;Product&quot; ])' name='shop'/>
                                  
                                  <b:include name='snippetedPostContent'/>
                                </article>
                              </b:loop>
                            </div>
                          </b:includable>
                        </b:widget>
                        <b:widget id='Label00' locked='false' title='Labels' type='Label' version='2' visible='true'>
                          <b:widget-settings>
                            <b:widget-setting name='sorting'>ALPHA</b:widget-setting>
                            <b:widget-setting name='display'>LIST</b:widget-setting>
                            <b:widget-setting name='selectedLabelsList'/>
                            <b:widget-setting name='showType'>ALL</b:widget-setting>
                            <b:widget-setting name='showFreqNumbers'>true</b:widget-setting>
                          </b:widget-settings>
                          <b:includable id='main' var='this'>
                            <b:include name='widget-title'/>
                            <b:include name='content'/>
                          </b:includable>
                          <b:includable id='cloud'>
                            <b:if cond='data:this.showFreqNumbers'>
                              <span class='count fontSm shrink' expr:data-text='&quot;(&quot; + data:label.count + &quot;)&quot;'/>
                            </b:if>
                          </b:includable>
                          <b:includable id='content'>
                            <div class='itemL cInherit fontS'>
                              <b:class expr:name='data:this.display'/>
                              <b:tag class='labi hidden' cond='data:labels.length &gt; (7 + 1)' expr:id='data:widget.instanceId + &quot;-in&quot;' name='input' type='checkbox'/>
                              
                              <b:tag class='lab flex wrap' name='div'>
                                <b:class cond='data:this.display == &quot;list&quot;' name='list'/>
                                <b:loop index='list' values='data:labels' var='label'>
                                  <b:if cond='data:label.name != &quot;Discount10&quot; and data:label.name != &quot;Discount20&quot; and data:label.name != &quot;Discount30&quot; and data:label.name != &quot;Discount40&quot; and data:label.name != &quot;Discount50&quot; and data:label.name != &quot;Discount60&quot; and data:label.name != &quot;Discount70&quot; and data:label.name != &quot;Discount80&quot; and data:label.name != &quot;Discount90&quot;'>
                                    <div>
                                      <b:class cond='data:this.display != &quot;list&quot;' expr:name='&quot;s-&quot; + data:label.cssSize'/>
                                    
                                      <b:comment>Showing only 8 lists</b:comment>
                                      <b:class cond='data:list &lt;= 7' name='s'/>
                          
                                      <b:tag class='link flex space-between' expr:name='data:blog.url != data:label.url ? &quot;a&quot; : &quot;div&quot;'>
                                        <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.url' name='href'/>
                                        <b:attr cond='data:blog.url != data:label.url' expr:value='data:label.name' name='aria-label'/>
                                        <b:class cond='data:this.display != &quot;list&quot;' name='c'/>
                                
                                        <b:comment>Activate to remove background color</b:comment>
                                        <b:class cond='data:this.display == &quot;list&quot;' name='noBg'/>
                        
                                        <span class='name ellips'><data:label.name/></span>
                                      
                                        <b:if cond='data:this.display == &quot;list&quot;'>
                                          <b:include name='list'/>
                                          <b:else/>
                                          <b:include name='cloud'/>
                                        </b:if>
                                      
                                      </b:tag>
                                    
                                    </div>
                                  </b:if>
                                </b:loop>
                              </b:tag>
                              
                              <b:comment>Show/hide label</b:comment>
                              <b:tag aria-label='Show all labels' class='flexIn baseline' cond='data:labels.length &gt; (7 + 1)' expr:data-hide='data:messages.showLess' expr:data-length='&quot;(+&quot; + (data:labels.length - (7 + 1)) + &quot;)&quot;' expr:data-show='data:messages.showAll' expr:for='data:widget.instanceId + &quot;-in&quot;' name='label'/>
                              
                            </div>
                          </b:includable>
                          <b:includable id='list'>
                            <span class='count fontSm flexIn center shrink op i16'>
                              <b:attr cond='data:this.showFreqNumbers' expr:value='data:label.count' name='data-text'/>
                              <b:include name='tag-right-icon'/>
                            </span>
                          </b:includable>
                        </b:widget>
                        <b:widget cond='!data:view.isPreview and data:view.isPost' id='HTML11' locked='true' title='Table of Content' type='HTML' version='2' visible='true'>
                          <b:widget-settings>
                            <b:widget-setting name='content'/>
                          </b:widget-settings>
                          <b:includable id='main'>
                            <b:tag class='tocI hidden' id='forTOC' name='input' type='checkbox'/>
                            <div class='tocP'>
                              <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                              <div class='tocIn noList'>
                                <label aria-label='Close' class='tocH flexIn fontM op i16' for='forTOC'>
                                  <b:if cond='data:blog.languageDirection != &quot;rtl&quot;'>
                                    <b:include name='arrow-left-1-icon'/>
                                    <b:else/>
                                    <b:include name='arrow-right-1-icon'/>
                                  </b:if>
                                </label>
                        
                                <div class='tocC cInherit u' id='tocAuto'>
                                  <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                                </div>
                              </div>
                            </div>
                    
                            <label aria-label='Open table of content' class='tocB fc' for='forTOC'>
                              <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                              <span class='flex center op i22'><b:include name='document-icon'/></span>
                            </label>
                    
                            <b:comment>Script to activate ToC (Table of Content) feature</b:comment>
                            <script>/*<![CDATA[*/ document.addEventListener('DOMContentLoaded', () => new TableOfContents({ from: document.querySelector('#postBody'), to: document.querySelector('#tocAuto') }).generateToc() ); /*]]>*/</script>
                          </b:includable>
                        </b:widget>
                      </b:section>
                      
                      <b:comment>Sidebar with sticy effect</b:comment>
                      <b:section class='sideSticky flex column' id='side-sticky' showaddelement='true'>
                        <b:widget cond='!data:view.isPreview and !data:blog.isMobileRequest' id='HTML95' locked='true' title='Sticky ad placement(desktop only)' type='HTML' version='2' visible='false'>
                          <b:widget-settings>
                            <b:widget-setting name='content'/>
                          </b:widget-settings>
                          <b:includable id='main'>
                            <b:if cond='data:content != &quot;&quot;'>
                              <data:content/>
                          
                              <b:else/>
                              <!--[ Blank ad ]-->
                              <div class='adB' expr:data-text='data:messages.adsGoHere'/>
                            </b:if>
                          </b:includable>
                        </b:widget>
                        <b:widget id='LinkList1' locked='true' title='Additional menu' type='LinkList' version='2' visible='true'>
                          <b:widget-settings>
                            <b:widget-setting name='link-5'> # Skype</b:widget-setting>
                            <b:widget-setting name='link-3'>#</b:widget-setting>
                            <b:widget-setting name='link-4'> # LinkedIn</b:widget-setting>
                            <b:widget-setting name='text-1'>Disclaimer</b:widget-setting>
                            <b:widget-setting name='text-0'>Term</b:widget-setting>
                            <b:widget-setting name='text-3'>Faq</b:widget-setting>
                            <b:widget-setting name='text-2'>Privacy</b:widget-setting>
                            <b:widget-setting name='text-5'>skype</b:widget-setting>
                            <b:widget-setting name='text-4'>linkedin</b:widget-setting>
                            <b:widget-setting name='sorting'>NONE</b:widget-setting>
                            <b:widget-setting name='link-1'>#</b:widget-setting>
                            <b:widget-setting name='link-2'>#</b:widget-setting>
                            <b:widget-setting name='link-0'>#</b:widget-setting>
                          </b:widget-settings>
                          <b:includable id='main'>
                            <b:include name='content'/>
                          </b:includable>
                          <b:includable id='content'>
                            <ul class='addNav noList flex wrap fontS cInherit u'>
                              <b:loop values='data:links' var='link'>
                                <li><a expr:href='data:link.target'><data:link.name/></a></li>
                              </b:loop>
                            </ul>
                          </b:includable>
                        </b:widget>
                      </b:section>
                    </aside>
                  </b:if>
                  
                </div>
                
              </b:tag>
              
            </div>
          
            <b:comment><!--[ Mobile menu ]--></b:comment>
            <b:section class='mainM' cond='data:view.isLayoutMode or data:blog.isMobileRequest' id='mobile-menu' maxwidgets='1' showaddelement='false'>
              <b:widget id='LinkList99' locked='true' title='Mobile menu' type='LinkList' version='2' visible='true'>
                <b:widget-settings>
                  <b:widget-setting name='link-3'>custom_text</b:widget-setting>
                  <b:widget-setting name='sorting'>NONE</b:widget-setting>
                  <b:widget-setting name='link-4'>custom_text</b:widget-setting>
                  <b:widget-setting name='text-1'>Search</b:widget-setting>
                  <b:widget-setting name='link-1'>custom_text</b:widget-setting>
                  <b:widget-setting name='text-0'>Home</b:widget-setting>
                  <b:widget-setting name='link-2'>custom_text</b:widget-setting>
                  <b:widget-setting name='text-3'>Share</b:widget-setting>
                  <b:widget-setting name='link-0'>custom_text</b:widget-setting>
                  <b:widget-setting name='text-2'>Menu</b:widget-setting>
                  <b:widget-setting name='text-4'>Comments</b:widget-setting>
                </b:widget-settings>
                <b:includable id='main'>
                  <b:include name='content'/>
                </b:includable>
                <b:includable id='content'>
                  <div class='mobileM cInherit flex center'>
                    <b:class cond='!data:view.isPost' name='index'/>
                    
                    <b:loop index='mobile' values='data:links' var='link'>
                      <b:if cond='data:mobile &lt;= &quot;2&quot;'>
                        <div class='flex grow'>
                          <b:class cond='data:link.name == &quot;Home&quot;' name='home'/>
                          <b:class cond='data:link.name == &quot;Search&quot;' name='search'/>
                          <b:class cond='data:link.name == &quot;Menu&quot;' name='menu'/>
                        
                          <b:if cond='data:link.name == &quot;Home&quot;'>
                            <b:tag class='flex wrap opacity i20' expr:data-text='data:link.name' expr:name='data:view.url == data:blog.homepageUrl ? &quot;div&quot; : &quot;a&quot;'>
                              <b:attr cond='data:view.url != data:blog.homepageUrl' expr:value='data:link.name' name='aria-label'/>
                              <b:attr cond='data:view.url != data:blog.homepageUrl' expr:value='data:blog.homepageUrl.canonical' name='href'/>
                              <b:attr cond='data:view.url != data:blog.homepageUrl' name='role' value='button'/>
                            
                              <b:attr cond='data:link.target != &quot;#&quot; and data:link.target != &quot;custom_text&quot;' expr:value='data:link.target' name='data-text'/>
                              <b:include name='home-2-icon'/>
                            </b:tag>
                          
                            <b:elseif cond='data:link.name == &quot;Search&quot;'/>
                            <label class='flex wrap opacity i20' expr:data-text='data:link.name' for='forSearch'>
                              <b:attr cond='data:link.target != &quot;#&quot; and data:link.target != &quot;custom_text&quot;' expr:value='data:link.target' name='data-text'/>
                              <b:include name='search-icon'/>
                            </label>
                          
                            <b:elseif cond='data:link.name == &quot;Menu&quot;'/>
                            <label class='flex wrap opacity i20' expr:data-text='data:link.name' for='forNav'>
                              <b:attr cond='data:link.target != &quot;#&quot; and data:link.target != &quot;custom_text&quot;' expr:value='data:link.target' name='data-text'/>
                              <b:include name='category-2-icon'/>
                            </label>
                          
                          </b:if>
                        </div>
                      </b:if>
                    </b:loop>
                    
                    <b:if cond='data:view.isPost'>
                      <b:loop values='data:links' var='link'>
                        <b:if cond='data:link.name == &quot;Share&quot;'>
                          <div class='flex grow share'>
                            <label class='flex wrap op i20' expr:data-text='data:link.name' for='forShare'>
                              <b:attr cond='data:link.target != &quot;#&quot; and data:link.target != &quot;custom_text&quot;' expr:value='data:link.target' name='data-text'/>
                              <b:include name='export-icon'/>
                            </label>
                          </div>
                          
                          <b:elseif cond='data:link.name == &quot;Comments&quot;'/>
                          <div class='flex grow comment'>
                            <a class='flex wrap op i20' expr:data-text='data:link.name' href='#comment' role='button'>
                              <b:attr cond='data:link.target != &quot;#&quot; and data:link.target != &quot;custom_text&quot;' expr:value='data:link.target' name='data-text'/>
                              <b:include name='message-text-icon'/>
                            </a>
                          </div>
                        </b:if>
                      </b:loop>
                      
                      <b:else/>
                      
                      <b:loop values='data:links' var='link'>
                        
                        <b:comment>Your custom button here</b:comment>
                        
                      </b:loop>
                    </b:if>
                    
                  </div>
                </b:includable>
              </b:widget>
            </b:section>
          
            <!--[ Footer ]-->
            <footer class='mainF cInherit u noPrint'>
              <b:tag class='maxC' name='div'>
            
                <b:comment><!--[ Credit ]--></b:comment>
                <b:section class='credits flex' id='credit-widget' maxwidgets='2' showaddelement='false'>
                  <b:widget id='HTML88' locked='true' title='Credit' type='HTML' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='content'/>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <div class='credit fontM ellips'>
                        <b:class cond='data:blog.languageDirection == &quot;rtl&quot;' name='r'/>
                        <span class='cd'>
                          <b:class cond='data:content == &quot;&quot;' name='e'/>
                          <b:if cond='data:content == &quot;&quot;'>
                            <b:comment>Default credit</b:comment>
                            <span id='thisY'><script>/*<![CDATA[*/ document.getElementById("thisY").innerHTML = new Date().getFullYear() + "."; /*]]>*/</script></span>
                            <bdi><a expr:href='data:blog.homepageUrl.canonical'><b:eval expr='data:blog.title'/></a>.</bdi>
                          
                            <b:else/>
                            <data:content/>
                          </b:if><b:if cond='data:blog.url == data:blog.homepageUrl'> | Theme By <a href='https://www.mrskt.com/' rel='dofollow' target='_blank' title='MRSKT'>MRSKT</a> 
</b:if>
                        </span>
                      </div>
                    </b:includable>
                  </b:widget>
                  <b:widget id='TextList88' locked='true' title='Back to top' type='TextList' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='shownum'>1</b:widget-setting>
                      <b:widget-setting name='sorting'>NONE</b:widget-setting>
                      <b:widget-setting name='item-0'>Top</b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <b:include name='content'/>
                    </b:includable>
                    <b:includable id='content'>
                      <b:loop index='b' values='data:items' var='item'>
                        <b:if cond='data:b &lt;= 0'>
                          <b:tag class='bT flex fontS noWrap opacity i14 noJava' expr:data-text='data:item' name='div'>
                            <b:attr name='onclick' value='window.scrollTo({top: 0});'/>
                            <b:include name='arrow-up-1-icon'/>
                          </b:tag>
                          <noscript>
                            <b:tag class='bT flex fontS noWrap opacity i14' expr:aria-label='data:item' expr:data-text='data:item' href='#nB' name='a'>
                              <b:include name='arrow-up-1-icon'/>
                            </b:tag>
                          </noscript>
                        </b:if>
                      </b:loop>
                    </b:includable>
                  </b:widget>
                  <b:widget id='LinkList88' locked='true' title='Social media' type='LinkList' version='2' visible='true'>
                    <b:widget-settings>
                      <b:widget-setting name='text-10'>Line</b:widget-setting>
                      <b:widget-setting name='shownum'>4</b:widget-setting>
                      <b:widget-setting name='sorting'>NONE</b:widget-setting>
                      <b:widget-setting name='link-1'>#</b:widget-setting>
                      <b:widget-setting name='link-13'>#</b:widget-setting>
                      <b:widget-setting name='link-2'>#</b:widget-setting>
                      <b:widget-setting name='link-12'>#</b:widget-setting>
                      <b:widget-setting name='link-0'>#</b:widget-setting>
                      <b:widget-setting name='link-11'>#</b:widget-setting>
                      <b:widget-setting name='link-10'>#</b:widget-setting>
                      <b:widget-setting name='text-9'>Tiktok</b:widget-setting>
                      <b:widget-setting name='link-9'>#</b:widget-setting>
                      <b:widget-setting name='text-8'>Messenger</b:widget-setting>
                      <b:widget-setting name='link-7'>#</b:widget-setting>
                      <b:widget-setting name='link-8'>#</b:widget-setting>
                      <b:widget-setting name='link-5'>#</b:widget-setting>
                      <b:widget-setting name='link-6'>#</b:widget-setting>
                      <b:widget-setting name='link-3'>#</b:widget-setting>
                      <b:widget-setting name='link-4'>#</b:widget-setting>
                      <b:widget-setting name='text-1'>Instagram</b:widget-setting>
                      <b:widget-setting name='text-0'>Facebook</b:widget-setting>
                      <b:widget-setting name='text-3'>Youtube</b:widget-setting>
                      <b:widget-setting name='text-2'>Twitter</b:widget-setting>
                      <b:widget-setting name='text-5'>Pinterest</b:widget-setting>
                      <b:widget-setting name='text-4'>LinkedIn</b:widget-setting>
                      <b:widget-setting name='text-7'>Telegram</b:widget-setting>
                      <b:widget-setting name='text-6'>Whatsapp</b:widget-setting>
                      <b:widget-setting name='text-11'>Dribbble</b:widget-setting>
                      <b:widget-setting name='text-12'>Tumblr</b:widget-setting>
                      <b:widget-setting name='text-13'>Github</b:widget-setting>
                    </b:widget-settings>
                    <b:includable id='main'>
                      <b:include name='content'/>
                    </b:includable>
                    <b:includable id='content'>
                      <div class='socials flex'>
                        <b:loop index='socials' values='data:links' var='link'>
                          <b:if cond='(!data:blog.isMobileRequest and data:socials &lt;= 3) or (data:blog.isMobileRequest and data:socials &lt;= 2)'>
                            <b:tag class='ic op i20' expr:name='data:link.target != &quot;#&quot; ? &quot;a&quot; : &quot;div&quot;'>
                              <b:attr cond='data:link.target != &quot;#&quot;' expr:value='data:link.name' name='aria-label'/>
                              <b:attr cond='data:link.target != &quot;#&quot;' expr:value='data:link.target' name='href'/>
                              <b:attr cond='data:link.target != &quot;#&quot;' name='target' value='_blank'/>
                              <b:attr cond='data:link.target != &quot;#&quot;' name='rel' value='noopener'/>
                              <b:attr cond='data:link.target != &quot;#&quot;' name='role' value='button'/>
                              
                              <b:if cond='data:link.name == &quot;Facebook&quot;'>
                                <b:include name='facebook-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Instagram&quot;'/>
                                <b:include name='instagram-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Twitter&quot;'/>
                                <b:include name='twitter-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Youtube&quot;'/>
                                <b:include name='youtube-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;LinkedIn&quot;'/>
                                <b:include name='linkedin-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Pinterest&quot;'/>
                                <b:include name='pinterest-i-icon'/>
                            
                                <b:elseif cond='data:link.name == &quot;Whatsapp&quot;'/>
                                <b:include name='whatsapp-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Telegram&quot;'/>
                                <b:include name='telegram-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Messenger&quot;'/>
                                <b:include name='messenger-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Tiktok&quot;'/>
                                <b:include name='tiktok-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Line&quot;'/>
                                <b:include name='line-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Dribbble&quot;'/>
                                <b:include name='dribbble-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Tumblr&quot;'/>
                                <b:include name='tumblr-i-icon'/>
                              
                                <b:elseif cond='data:link.name == &quot;Github&quot;'/>
                                <b:include name='github-b-icon'/>
                              
                                <b:else/>
                                <b:include name='blank-s-icon'/>
                              </b:if>
                              
                            </b:tag>
                          </b:if>
                        </b:loop>
                      </div>
                    </b:includable>
                  </b:widget>
                </b:section>
              </b:tag>
            </footer>
            
          </div>
        </div>
          
      </b:tag>
    </b:if>
    
    <b:if cond='!data:view.isPreview and !data:view.isError'>
      <b:comment><!--[ Delete (or data:blog.isMobileRequest) if you want to show ad in both(desktop and mobile) ]--></b:comment>
      <b:section class='noPrint' cond='data:view.isLayoutMode or data:blog.isMobileRequest' id='anchor-ad' max-widget='2' showaddelement='false'>
        <b:widget id='HTML99' locked='true' title='Anchor ad placement(mobile only)' type='HTML' version='2' visible='false'>
          <b:widget-settings>
            <b:widget-setting name='content'/>
          </b:widget-settings>
          <b:includable id='main'>
            <!--[ Sticky ad ]-->
            <details class='stickAd' open=''>
              <summary aria-label='Close ad' class='flex center n'/>
              
              <div class='stickC'>
                <b:if cond='data:content != &quot;&quot;'>
                  <data:content/>
                  
                  <b:else/>
                  <!--[ Blank ad ]-->
                  <div class='adB' expr:data-text='data:messages.adsGoHere'/>
                </b:if>
              </div>
            </details>
          </b:includable>
        </b:widget>
      </b:section>
    </b:if>
    
    <b:comment><!--[ Cookie consent(if necessary) ]--></b:comment>
    <b:section class='noPrint' cond='!data:view.isError' id='cookie-consent' max-widget='1' showaddelement='false'>
      <b:widget id='LinkList404' locked='true' title='Cookie consent' type='LinkList' version='2' visible='false'>
        <b:widget-settings>
          <b:widget-setting name='sorting'>NONE</b:widget-setting>
          <b:widget-setting name='text-1'>Learn more</b:widget-setting>
          <b:widget-setting name='link-1'>#</b:widget-setting>
          <b:widget-setting name='text-0'>Text</b:widget-setting>
          <b:widget-setting name='link-2'>custom_text</b:widget-setting>
          <b:widget-setting name='link-0'>We use cookies to understand how you use our site and improve your experience. This includes personalized content and advertising....</b:widget-setting>
          <b:widget-setting name='text-2'>Accept</b:widget-setting>
        </b:widget-settings>
        <b:includable id='main'>
          <b:include name='content'/>
        </b:includable>
        <b:includable id='content'>
          <div class='nJ cookie'>
            <p>
              <b:loop index='i' values='data:links' var='link'>
                <b:if cond='data:i &lt;= 1'>
                  <b:if cond='data:link.name == &quot;Text&quot;'>
                    <span class='opacity'><data:link.target/></span>
                  </b:if>
                  <b:if cond='data:i == 1'>
                    <a class='extL opacity' expr:aria-label='data:link.name' expr:data-text='data:link.name' expr:href='data:link.target' rel='noreferrer' target='_blank'><data:link.name/></a>
                  </b:if>
                </b:if>
              </b:loop>
            </p>
            <div class='flex ft'>
              <b:loop index='i' values='data:links' var='link'>
                <b:if cond='data:link.name == &quot;Accept&quot;'>
                  <span class='acc'>
                    <b:if cond='data:link.target != &quot;#&quot; and data:link.target != &quot;custom_text&quot;'>
                      <data:link.target/>
                      <b:else/>
                      <data:link.name/>
                    </b:if>
                  </span>
                </b:if>
              </b:loop>
            </div>
          </div>
          
          <script>/*<![CDATA[*/ const cookieBox = document.querySelector(".nJ.cookie"), acceptBtn = cookieBox.querySelector(".acc"); acceptBtn.onclick = ()=> {document.cookie = "cookie=Notification; max-age="+60*60*24*30; if(document.cookie) {cookieBox.classList.add("hidden");} else {alert("Cookie can't be set! Please unblock this site from the cookie setting of your browser."); } }; let checkCookie = document.cookie.indexOf("cookie=Notification"); checkCookie != -1 ? cookieBox.classList.add("hidden") : cookieBox.classList.remove("hidden"); /*]]>*/</script>
        </b:includable>
      </b:widget>
    </b:section>
    
    <b:if cond='data:view.isLayoutMode or data:view.isError'>
    <b:tag class='errorP flex' name='section'>
      <b:section class='errorC' id='error-404' showaddelement='false'>
        <b:widget id='TextList404' locked='true' title='Take me back' type='TextList' version='2' visible='true'>
          <b:widget-settings>
            <b:widget-setting name='shownum'>3</b:widget-setting>
            <b:widget-setting name='sorting'>NONE</b:widget-setting>
            <b:widget-setting name='item-2'><![CDATA[We can't seem to find the page you are looking for, we'll fix that soon but for now you can return to the home page]]></b:widget-setting>
            <b:widget-setting name='item-1'><![CDATA[Something's wrong]]></b:widget-setting>
            <b:widget-setting name='item-0'>&#175;\_(ツ)_/&#175;</b:widget-setting>
          </b:widget-settings>
          <b:includable id='main'>
            <b:include name='content'/>
          </b:includable>
          <b:includable id='content'>
            
            <b:loop index='error' values='data:items' var='item'>
              <b:if cond='data:error &lt;= 2'>
                <b:tag expr:name='data:error == 0 or data:error == 1 ? &quot;div&quot; : &quot;p&quot;'>
                  <b:attr expr:value='data:error == 0 and data:error != 2 ? &quot;e&quot; : &quot;t&quot;' name='class'/>
                  <b:attr cond='data:error == 2' name='class' value='opacity'/>
                  <data:item/>
                </b:tag>
              </b:if>
            </b:loop>
            
            <b:comment><!--[ Homepage button ]--></b:comment>
            <a class='button' expr:aria-label='data:title' expr:href='data:blog.homepageUrl.canonical'>
              <b:comment><!--[ Remove tag bellow to change button style, or you can try to replace/add the attribute with name='round' ]--></b:comment>
              <b:class name='ln'/>
            </a>
            
          </b:includable>
        </b:widget>
      </b:section>
    </b:tag>
    </b:if>
    
    <!--[ If Javascript is disabled ]-->
    <noscript>
      <details class='nJ' open=''>
        <summary class='n'><span class='c' data-text='Ignore it'/></summary>
        <span data-text='This website requires Javascript for better experience, some features may not work properly.'/>
      </details>
    </noscript>
    
    <b:if cond='!data:view.isPreview and !data:view.isError'>
      <b:comment><!--[ Load More - Delete this section if you want to disable this feature ]--></b:comment>
      <b:include cond='data:view.isHomepage or data:view.url == data:blog.homepageUrl.canonical path &quot;search&quot;' name='postPaginationMore'/>
      
      <script>/*<![CDATA[*/ /*@shinsenter/defer.js*/ !function(c,i,t){var f,o=/^data-(.+)/,u='IntersectionObserver',r=/p/.test(i.readyState),s=[],a=s.slice,d='lazied',n='load',e='pageshow',l='forEach',m='hasAttribute',h='shift';function p(e){i.head.appendChild(e)}function v(e,n){a.call(e.attributes)[l](n)}function y(e,n,t,o){return o=(o=n?i.getElementById(n):o)||i.createElement(e),n&&(o.id=n),t&&(o.onload=t),o}function b(e,n){return a.call((n||i).querySelectorAll(e))}function g(t,e){b('source',t)[l](g),v(t,function(e,n){(n=o.exec(e.name))&&(t[n[1]]=e.value)}),e&&(t.className+=' '+e),n in t&&t[n]()}function I(e){f(function(o){o=b(e||'[type=deferjs]'),function e(n,t){(n=o[h]())&&(n.parentNode.removeChild(n),(t=y(n.nodeName)).text=n.text,v(n,function(e){'type'!=e.name&&(t[e.name]=e.value)}),t.src&&!t[m]('async')?(t.onload=t.onerror=e,p(t)):(p(t),e()))}()})}(f=function(e,n){r?t(e,n):s.push(e,n)}).all=I,f.js=function(n,t,e,o){f(function(e){(e=y('SCRIPT',t,o)).src=n,p(e)},e)},f.css=function(n,t,e,o){f(function(e){(e=y('LINK',t,o)).rel='stylesheet',e.href=n,p(e)},e)},f.dom=function(e,n,t,o,i){function r(e){o&&!1===o(e)||g(e,t)}f(function(t){t=u in c&&new c[u](function(e){e[l](function(e,n){e.isIntersecting&&(n=e.target)&&(t.unobserve(n),r(n))})},i),b(e||'[data-src]')[l](function(e){e[m](d)||(e.setAttribute(d,''),t?t.observe(e):r(e))})},n)},f.reveal=g,c.Defer=f,c.addEventListener('on'+e in c?e:n,function(){for(I();s[0];t(s[h](),s[h]()))r=1})}(this,document,setTimeout),function(e,n){e.defer=n=e.Defer,e.deferscript=n.js,e.deferstyle=n.css,e.deferimg=e.deferiframe=n.dom}(this); /*]]>*/</script>
      <script id='polyfill-js'>/*<![CDATA[*/ 'IntersectionObserver'in window||document.write('<script src="https://polyfill.io/v3/polyfill.min.js?features=IntersectionObserver"><\/script>'); /*]]>*/</script>
      
      <b:comment><!--[ Additional script ]--></b:comment>
      <b:include name='allJavascript'/>
      <b:include cond='data:view.isPost' name='copyCodeToClipboard'/>
      <b:include name='bookmarkLoad'/>
      
    </b:if>
    
  <!--[ </body> close ]-->
  <b:if cond='!data:view.isPreview'>&lt;!--</b:if></body><b:if cond='!data:view.isPreview'>--&gt;&lt;/body&gt;</b:if>
</html>
